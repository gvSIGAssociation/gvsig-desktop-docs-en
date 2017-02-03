Use gvSIG to develop gvSIG
==========================

Until version 2, the main way to develop
gvSIG was through the creation of a workspace with the sources of the official distribution. These and quite some knowledge was necessary to build a full gvSIG distribution.

Although some efforts were made to develop plugins without having a full gvSIG workspace, it was not until version 2 that the mechanism worked properly, so that the strong recommendation was to base plugin development on the complete gvSIG sources.

In version 2, to develop a new plugin, one can base on the binary installation of gvSIG, maintaining in the development workspace only the development projects and
deploying them in the existing installation.

Besides this, in version 2, a considerable effort has been made to make the libraries that gvSIG uses for the plugin engine independent.

This allows us to perform much of the developing
without the need for gvSIG directly.
Small applications can be written by just using the gvSIG libraries can be run independently.

If you have already developed for gvSIG 1, keep in mind
that the development mode has changed. 
It is not necessary to create a workspace with the sources and to compile gvSIG itself. That is necessary only if one need to change gvSIG core code. 

So functionalities can be developed in an own plugin instead of having to modify the gvSIG code.
If fixes or changes to gvSIG itself are required, developers can send patches that will be reviewed and included in future gvSIG versions.
