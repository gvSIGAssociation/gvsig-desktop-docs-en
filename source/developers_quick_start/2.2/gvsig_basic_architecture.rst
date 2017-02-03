
gvSIG basic architecture
========================

org.gvsig.tools
---------------

The *tools* library is an important piece of gvSIG.
It provides a number of utilities and services on which the other gvSIG modules rely on. The main functionalities provided are:

- Registration of extension points
- Libraries initialization
- Utilities for the separation of API and implementation (registry of APIs, registry of API implementations, registry of SPI service providers or locatlization of an API implementation)
- Jobs Monitoring

Although these are the most important services provided by the library, it also provides other utilities that can be considered structural to the application. 

Examples are:

- Disposables
- Interfaces for the management of Observers-observables
- Interfaces for the handling of visitors
- Definition of data types
- Basis Interfaces for evaluators
- Persistence of Objects

..  tip::
    
    You can find more detailed information on how the gvSIG libraries mechanism works in org.gvsig.tools.library_, on the use of *locators* look in org.gvsig.tools.locator_, and for the *managers* one can find documentation in org.gvsig.tools.service_.

Let's have a look at three basic concepts that will be repeated several times in the code that we will see and will allow us to strictly separate the API from the implementation:

- **Libraries**. These are pieces of code that provide functionality and are usually bundled in a *jar* file. Each of these libraries must have a class that implements the *Library* interface, usually extending the *AbstractLibrary* class. They have methods to initialize the library they are in charge of.

- **Managers**. These are components that provide functionality to the application, acting as a factory for various services the library offers and for the configuration of those. They act as singletons because usually there is only one application instance for each of these components. Any library will have one or more of these according to its internal logic.
  
- **Locators**. This is an utility that lets you register implementations of *managers* for a given library, as well as recover a *Manager* implementation of a particular API.

These three pieces need to be kept in mind whenever we want to use or create new components as they are artifacts that will allow us to access the various parts of gvSIG.

.. _`org.gvsig.tools.library` : https://gvsig.org/web/reference_catalog/lookupObject?uuid=603a7a0d9e4f0f0306401bd3c238a89d

.. _`org.gvsig.tools.service` : https://gvsig.org/web/reference_catalog/lookupObject?uuid=0aa6c6f67612c991f723fd8f4e069937

.. _`org.gvsig.tools.locator` : https://gvsig.org/web/reference_catalog/lookupObject?uuid=f628030a648208d04db33e339ba79176



Andami, the plugins framework
-----------------------------

*Andami* is the framework that gvSIG uses to build the application.
Mainly it provides two services, on the one hand the management and loading of *plugins* and on the other hand the management of the graphical user interface windows.

At this point let's focus a little bit on the management of the *plugins*.
*Andami* provides the application launcher that initializes the *plugins* engine and is responsible for the loading of the *plugins* that are installed in the application. A *plugin* is a functional unit that can provide:

- menu item to add to the application
- new buttons and toolbars
- new data providers
- new document types

Usually, in an gvSIG installation we find the folder *gvSIG/extensiones*. This folder contains the various *plugins* that are installed in the application. Each *plugin* is contained in a folder, inside which we always find at least the following files:

- **config.xml**, It is mandatory that exists. Identifies the folder as a plugin. It contains  information about:

  - where the classes of that plugin are

    ..  tip::
        One can find more information on the structure and the various tags allowed in the `config.xml file`_

    .. _`config.xml file`: http://docs.gvsig.org/web/reference_catalog/lookupObject?uuid=4137884c37a68ee8cd685248f7f12cc1

  - That classes that must be loaded as *extensions* (IExtension).
  - whether the plugin depends on another plugin
  - which menu options the plugin adds to the application
  - which toolbars and buttons the plugin adds.

  
- **package.info**, which gives information about the version, name, id or description of the plugin. It acts like a metadata container for the plugin and allows us to identify the plugin in case of update or reinstall.

Additionally we may find a folder **theme**, which is the configuration the splash screen of the application, the windows icons and background colors.

Although the mechanism for adding new functionality to gvSIG is the addition of new plugins, these can in turn contain one or more *extensions*. The extensions itself are the ones implementing the provided functionality. So, we will have a *plugin* that contains *extensions*.

In connection with the plugin management, the main parts we will fin are:

- **PluginsLocator**, which will give us access to the plugin-*manager* through a static *getManager* method.

- **PluginsManager**, which provides methods to examine what plugins are loaded and what extensions each of these have.

- The class **PluginsServices** that represents the instance of a given plugin.

- The **IExtension** interface, which represents an action or a block of actions to incorporate in gvSIG.

- The **ExclusiveUIExtension** interface, which allows us to control the visibility of all extensions loaded in the application.

Of these entities we will describe a little more the interface **IExtension** - This is the interface that we have to implement in order to add a new button or
menu option. In this interface we find the following methods:

- **initialize**: this method is executed when the extension is loaded at plugin initialization. Keep in mind that when this method is invoked is is possible that not all gvSIG extensions have been initialized. Usually here those extension components are initialized, that should be used by other extensions.

- **postInitilize**: it is invoked right after the *initialize* method of all gvSIG extensions has been invoked. Usually this will initialize those components of our extension that require other extensions.

- **terminate**: invoked when needed gvSIG dispose the extension. Normally this will occur at the shutdown of the application. Here we must ensure that system resources that our extension has reserved are released.

- **execute**: this method is executed whenever the user interacts with the menu or button in the toolbar associated with the extension. Normally this is where the execution of our functionality is implemented.

- **isEnable**: is invoked when you need to know if the user interface associated with the extension (buttons or menu options) needs to be enabled.

- **isVisible**: is invoked when you need to know if the user interface associated with the extension (buttons or menu options) has to be visible.


Windows
-------
..  tip::
    Although there is currently no related documentation for the version 2 of gvSIG, the existing documentation for gvSIG 1 is still valid.
    You can find it in `Andami Windows`_

.. _`Andami Windows`: http://docs.gvsig.org/web/reference_catalog/lookupObject?uuid=cb84e3369a85f0dcac645716079455d5


*Andami*, in addition to providing a mechanism for the loading and management of the *plugins*, also exposes an API for the management of application windows. Currently the paradigm used for managing windows is MDI. However the gvSIG window manager can be replaced to provide other display modes (SDI, tabs, ...).

The main entities that we find in the *andami* framework and related the windows management are:

- **MDIManagerFactory** is the factory where the MDIManager instance is registered and where you can get that instance (acts as Locator).

- **MDIManager** represents the window manager registered with gvSIG. It has methods to loda or close a window.

- **IWindow** is the interface a JPanel must implement to be usable as a window in gvSIG.

- **WindowInfo**, which provides our panels through the *IWindow* interface and defines the characteristics of our window (title, size, type, ...).

In general whenever we do not need to specify a finer control over our windows we can use the *showWindow* method of the *MDIManager* for making a window
from a standard *JPanel* swing.



Some gvSIG plugins
------------------

In gvSIG, we can find a number of plugins that provide the base functionalities of the application that are important to other plugins. These are:

- org.gvsig.app.mainplugin_. This plugin provides most of the generic application
  functionality of gvSIG as well as basic access to vector data. It provides:
  
  - the concept of the project and its documents
  - the document view
  - the basic tools to access vector data of the view
  
  This plugin along with the implementation of these features provides a *manager* 
  and a locator that are important for the development of other plugins:
  
  - **ApplicationManager**: this is a manager who provides us with access to other
    managers of the application as well as basic functionality for global access 
    to application resources. We can call it the object that 
    *represents the gvSIG application*.

  - **ApplicationLocator**, which is the locator that gives us access to the manager of the application (ApplicationManager).


- org.gvsig.app.document.table.app.mainplugin_

- org.gvsig.app.document.layout2.app.mainplugin_

- org.gvsig.vectorediting.app.mainplugin_ provides the functionality for the editing of tabular and vector data.

- org.gvsig.geodb.app.mainplugin_ adds to the application the support to access databases as for example PostgreSQL.

- org.gvsig.i18n.app.mainplugin_, adds to the application support for internationalization.

- org.gvsig.projection.app.jcrs_ adds support for CRS management.

- org.gvsig.raster.tools.app.basic_ adds raster support to gvSIG.


These are some of the most important plugins of gvSIG as they offer important base functionalities or are necessary for others plugins to work.

Besides these there are many more plugins plugins in the distribution of gvSIG which may be necessary or not based on what gvSIG is used for.

.. _org.gvsig.app.mainplugin: https://redmine.gvsig.net/redmine/projects/gvsig-desktop
.. _org.gvsig.app.document.table.app.mainplugin: https://redmine.gvsig.net/redmine/projects/gvsig-desktop
.. _org.gvsig.app.document.layout2.app.mainplugin: https://redmine.gvsig.net/redmine/projects/gvsig-app-document-layout
.. _org.gvsig.vectorediting.app.mainplugin: https://redmine.gvsig.net/redmine/projects/gvsig-vector-editing
.. _org.gvsig.geodb.app.mainplugin: https://redmine.gvsig.net/redmine/projects/gvsig-desktop
.. _org.gvsig.i18n.app.mainplugin: https://redmine.gvsig.net/redmine/projects/gvsig-desktop
.. _org.gvsig.projection.app.jcrs: https://redmine.gvsig.net/redmine/projects/gvsig-jcrs
.. _org.gvsig.raster.tools.app.basic: https://redmine.gvsig.net/redmine/projects/gvsig-raster


Some important libraries
------------------------

When developing gvSIG, it is good to know the existing plugins, especially the features offered by the *ApplicationManager*. But what really matters is to be aware of the libraries that we need to implement the wanted functionalities.

From gvSIG version 2.0.0 on important changes have been introduced in the way gvSIG is built as for example the naming used to identify projects and libraries that are created. However this migration has not been a quick process. It has been happening over the course of several years. This has resulted in a lack of uniformity in the naming of components existing at that time. 
When can check the name of a library from the Eclipse project name, the name of the jar generated by the Maven artifact name. In recently projects generated the choice was made that these three names should match, being the name taken from the Maven artifact. However in previous projects we find different names for each of these things. For the developer that wants to use gvSIG, the important thing is to know the Maven artifact name, because normally that is the name that needs to be set in the dependencies, while the project name is less relevant.


The libraries that are mostly needed from gvSIG are:

- **org.gvsig.tools.lib**: contains structural utilities. It has already been mentioned at the beginning of the document.

- **org.gvsig.fmap.geometry**: is the library to manage geometries. It contains a geometry model with a separate API and implementation.

..  tip::
    Although based on gvSIG 2.0.0, documentation related to data access and geometries which can be interesting to read and can be applied to almost all of gvSIG 2.2.0. can be found at `DAL`_ and here for the `geometries`_ part.

- **org.gvsig.projection**: is the library that manages coordinate reference systems in gvSIG.

- **org.gvsig.fmap.dal**: is the *Data Access Library* of gvSIG. It is used by all projects that in a way or another need to access a shapefile, dxf, PostgreSQL table, GML, a WFS layer or DGN file. It presents a common API to access vector and tabular data or to access raster data.

- **org.gvsig.fmap.mapcontext**: contains the API and implementation of map layers and logical levels.

- **org.gvsig.fmap.control**: contains the swing components that are bound to the DAL and mapcontext libraries. For example it could be a visual component to present a map or a table obtained from DAL.

- **org.gvsig.projection.jcrs**: is an implementation of the projections API of *org.gvsig.projection*.

- **org.gvsig.symbology.lib.api**: contains the API of the symbols library of gvSIG.

- **org.gvsig.ui**: is a library that houses a series of graphical components of general utility.


.. _DAL: http://docs.gvsig.org/plone/projects/gvsig-desktop/docs/devel/org.gvsig.fmap.dal/2.0.0
  
.. _geometries: http://docs.gvsig.org/plone/projects/gvsig-desktop/docs/devel/org.gvsig.fmap.geom/2.0.0

