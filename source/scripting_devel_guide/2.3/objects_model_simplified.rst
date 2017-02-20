Objects Model Simplified
========================

.. |mo1| image:: images/modelo_de_objetos_simplificado.png


Here we can see a schema of the most common use components from scripting, the relation between them and how could we access to them from our script. Besides, we can navigate through and see the java class information of each component by clicking on them.

.. note::

	For Java developers and users with UML knowledge. This diagram is made for users without knowledge neither in Java or UML. Its main purpose is not to be strict with the UML nomenclature, just to be understandable for everyone.
	
	
.. raw:: html

    <img class="mapping" style="max-width: none" src="../../_images/modelo_de_objetos_simplificado.png" usemap="#map" height="1143" width="1022" border="0">
    <map name="map">
      <!-- #$-:Image map file created by GIMP Image Map plug-in -->
      <!-- #$-:GIMP Image Map plug-in by Maurits Rijk -->
      <!-- #$-:Please do not edit lines starting with "#$" -->
      <!-- #$VERSION:2.3 -->
      <!-- #$AUTHOR:Joaquin del Cerro Murciano --> 
	  <area shape="rect" coords="328,96,411,136" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/app/project/Project.html">
      <area shape="rect" coords="326,169,406,216" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/app/project/documents/Document.html">
      <area shape="rect" coords="315,303,427,346" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/app/project/documents/view/ViewDocument.html">
      <area shape="rect" coords="324,433,416,474" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/fmap/mapcontext/MapContext.html">
      <area shape="rect" coords="325,516,498,605" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/fmap/mapcontext/layers/FLayers.html">
      <area shape="rect" coords="316,683,390,719" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/fmap/mapcontext/layers/FLyrDefault.html">
      <area shape="rect" coords="38,629,156,733" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/fmap/dal/feature/FeatureStore.html">
      <area shape="rect" coords="69,777,152,813" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/fmap/dal/feature/FeatureSet.html">
      <area shape="rect" coords="166,779,260,815" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/fmap/dal/feature/FeatureType.html">
      <area shape="rect" coords="75,891,216,953" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/fmap/dal/feature/Feature.html">
      <area shape="rect" coords="62,990,228,1061" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/fmap/dal/feature/EditableFeature.html">
      <area shape="rect" coords="372,894,450,925" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/fmap/geom/Geometry.html">
      <area shape="rect" coords="566,811,693,844" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/fmap/geom/GeometryLocator.html">
      <area shape="rect" coords="555,900,686,936" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/fmap/geom/GeometryManager.html">
      <area shape="rect" coords="40,242,162,279" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/app/project/documents/table/TableDocument.html">
      <area shape="rect" coords="579,235,704,266" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/app/project/documents/layout/LayoutDocument.html">
      <area shape="rect" coords="588,309,693,341" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/app/project/documents/layout/LayoutContext.html">
      <area shape="rect" coords="606,380,747,416" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/app/project/documents/layout/fframes/FFrame.html">
      <area shape="rect" coords="547,437,640,472" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/app/project/documents/layout/fframes/FFrameView.html">
      <area shape="rect" coords="654,540,760,576" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/app/project/documents/layout/fframes/FFramePicture.html">
      <area shape="rect" coords="604,502,691,533" href="http://downloads.gvsig.org/download/gvsig-desktop-testing/dists/2.3.0/javadocs/html/org/gvsig/app/project/documents/layout/fframes/FFrameText.html">
    </map>
	

How to interpret the diagram
++++++++++++++++++++++++++++

In the last diagram we can see:

- **Yellow boxes**, represent a object that we can find and work with it.

- **Green boxes**, represent actions that we can use in our script. For example:

.. figure::  images/interpretar-funcion.png
   :align:   center
   
We will intrepret this as we have an available **function**, ``currentProject()``, that we can execute from our script to obtain its related object, in this case: **project**. For the elements labeled as **function** we will need import previously to its execution. In this case, this module where the ``currentProject()`` function is inside ``gvsig``::

    from gvsig import *

- **Blue boxes**, indicates that it's a abstract entity. We will never find an object of this type. These objects make reference to a generic group of objects with common features. For example, we have a :javadoc:`Document <Document>` that has the common features of :javadoc:`ViewDocument <ViewDocument>`, :javadoc:`TableDocument <TableDocument>` or :javadoc:`LayoutDocument <LayoutDocument>`. In this diagram we could find, for example:

.. figure::  images/interpretar-herencia.png
   :align:   center
   
Here we have an abstract entity :javadoc:`FFrame <FFrame>`, we will never find this type of object, what we will find is this object types: :javadoc:`FFrameView <FFrameView>`, :javadoc:`FFramePicture <FFramePicture>` or :javadoc:`FFrameText <FFrameText>`, and it show us that is related with :javadoc:`FFrame <FFrame>` They will have a common set of attributes and methods.

- **Relations between objects**, that show us how to get an object or a set of them from other one. For example:

.. figure::  images/interpretar-asociacion.png
   :align:   center

It show us that if we have an object :javadoc:`LayoutDocument <LayoutDocument>`, we could obtain a :javadoc:`LayoutContext <LayoutContext>` object using the ``getLaypoutContext`` method::

	laypoutContext = layoutDocument.getLaypoutContext()
