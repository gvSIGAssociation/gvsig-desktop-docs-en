Módulo commonsdialog
====================

Funciones principales
---------------------

.. py:function:: msgbox(message[,title="", meesageType=IDEA, root=None])

    Shows a message dialog with ok button only.

    :param str message: text to present in the dialog
    :param str title: title of the dialog
    :param int messageType: type of icon to use.
    :param root: Frame reference
    :type root: DefaultFrame or None

.. py:function:: inputbox(message, [title="", messageType=IDEA, initialValue="", root=None])

    Shows a input dialog.

    :param str message: text to present in the dialog
    :param str title: title of the dialog
    :param int messageType: type of icon to use.
    :param str initialValue: Initial value of the inputbox
    :param root: Frame reference
    :type root: DefaultFrame or None
    :return: Return text in the input box
    :rtype: str

.. py:function:: confirmDialog(message, [title="", optionType=YES_NO, messageType=IDEA, root=None])

    Create a message dialog with options button

    :param str message: text to present in the dialog
    :param str title: title of the dialog
    :param int optionType: bottons to show
    :param int messageType: type of icon to use.

.. py:function:: filechooser(option, [title="", initialPath=None, multiselection=False, filter = None, fileHidingEnabled=True, root=None])

	Allows configuration parameters to filechooser dialogs

    :param int option: file chooser selection mode. Allowed values: OPEN_FILE, OPEN_DIRECTORY, SAVE_FILE
    :param str title: Window title
    :param str initialPath: Initial path to the directory to open in the dialog
    :param boolean multiselection: Allow select more than one object.
    :param filter: list of acepted extension files ("jpg", "png", "gif")
    :type filter: List of Strings
    :param boolean fileHidingEnabled: True if hidden files are not displayed
    :return: Selected path or list of paths

.. py:function:: openFileDialog([title='', initialPath=None, root=None])

	Shows a window dialog to choose one file.

    :param str title: Window title. Default ''
    :param str initialPath: Initial path to open in window dialog

.. py:function:: openFolderDialog([title='', initialPath=None, root=None])

    Shows a window dialog to choose one folder.

    :param str title: Window title. Default ''
    :param str initialPath: Initial path to open in window dialog

.. py:function:: saveFileDialog([title='', initialPath=None, root=None])

    Shows a window dialog to choose one file.

    :param str title: Window title. Default ''
    :param str initialPath: Initial path to open in window dialog

.. py:function:: getJavaFile(path)

    Returns a java File using parameter path. If path doesn't exists looks for user home folder and if can not find it, returns path will be gvSIG instance directory.

    :param str path: String-path.
    :return: Return java.io.File

Constantes en la librería
-------------------------
Constantes que aparecen en la librería y usaremos en diferentes funciones::

	*messageType options*
	FORBIDEN = 0
	IDEA= 1
	WARNING= 2
	QUESTION= 3

	*Confirmdialog optionType Options*
	YES_NO = 0
	YES_NO_CANCEL = 1
	ACCEPT_CANCEL = 2

	YES = 0
	NO = 1
	CANCEL = 2

	*filechooser options*
	OPEN_FILE = 0
	OPEN_DIRECTORY = 1
	SAVE_FILE = 2

	*filechooser selectionMode*
	FILES_ONLY = JFileChooser.FILES_ONLY
	DIRECTORIES_ONLY = JFileChooser.DIRECTORIES_ONLY

Uso
---

En el módulo de commonsdialog gestiona las ventanas emergentes que aparecen en gvSIG. Por ejemplo, si queremos mostrar un avisa al usuario usaremos :py:func:`msgbox`: o si queremos preguntar por algún valor al usuario que ejecute el script, podemos usar la función :py:func:`inputbox` la cual devolverá el texto que escriba el usuario en la caja de texto que aparecerá en pantalla.

Para importar la librería lo haremos mediante::

	import gvsig.commonsdialog
	
o::

	from gvsig import commonsdialog
	
o::

	from gvsig.commonsdialog import *
	

	
Por ejemplo:

.. code-block:: python
	:linenos:
	:emphasize-lines: 1, 5
	
	from gvsig import commonsdialog

	def main(*args):

		commonsdialog.msgbox("Bienvenido a gvSig","Welcome", commonsdialog.IDEA)

El tipo de mensaje lo establecemos en el parámetro ``messageType`` como podemos ver en :py:func:`msgbox` y estos tipos se encuentran almacenados en constantes dentro del módulo ``commonsdialog``.

O depende de cómo lo importemos.

.. code-block:: python
	:linenos:
	:emphasize-lines: 1, 5
	:caption: msgbox.py
	:name: msgbox-commonsdialog
	
	from gvsig.commonsdialog import *

	def main(*args):

		msgbox("Bienvenido a gvSIG", "Welcome", IDEA)
		
Dando como resultado una ventana:

.. figure::  images/commonsdialog-msgbox_1.png
   :align:   center

Depende del tipo de aviso que seleccionemos mostrará diferentes iconos en la ventana:

WARNING:

.. figure::  images/commonsdialog-msgbox_2.png
   :align:   center
   
FORBIDEN:

.. figure::  images/commonsdialog-msgbox_3.png
   :align:   center
   
QUESTION:

.. figure::  images/commonsdialog-msgbox_4.png
   :align:   center
   
   
Tipos de diálogos
-----------------

Diferentes tipos de diálogos::

	from gvsig import *
	from gvsig import commonsdialog
	from gvsig.commonsdialog import *


	def main(*args):
		
		message = "Prueba"
		
		mb = commonsdialog.msgbox(message, title="", messageType=IDEA, root=None)
		print "msgbox:", mb

		ib = commonsdialog.inputbox(message, title="", messageType=IDEA, initialValue="", root=None)
		print "inputbox:", ib

		cd = commonsdialog.confirmDialog(message, title="", optionType=YES_NO, messageType=IDEA, root=None)
		print "confirmDialog:", cd

		option = "OPEN_FILE"
		fc = commonsdialog.filechooser(option, title="", initialPath=None,  multiselection=False, filter = None, fileHidingEnabled=True, root=None)
		print "filechooser:", fc

		fc = commonsdialog.filechooser(option, title="", initialPath=None,  multiselection=True, filter = None, fileHidingEnabled=True, root=None)
		print "filechooser:", fc

		ofiled = commonsdialog.openFileDialog(title='', initialPath=None, root=None)
		print "openFileDialog:", ofiled

		ofolderd = commonsdialog.openFolderDialog(title='', initialPath=None, root=None)
		print "openFolderDialog:", ofolderd
		
		sfd = commonsdialog.saveFileDialog(title='', initialPath=None, root=None)
		print "saveFileDialog:",sfd

Msgbox:

.. figure::  images/c_msgbox.png
   :align:   center

Inputbox:

.. figure::  images/c_inputbox.png
   :align:   center
   
Confirm Dialog:

.. figure::  images/c_confirmDialog.png
   :align:   center
		
File chooser:

.. figure::  images/c_1.png
   :align:   center
		
File chooser with multiselection:

.. figure::  images/c_2.png
   :align:   center
   
Open file dialog:

.. figure::  images/c_3.png
   :align:   center
   
Open folder dialog:

.. figure::  images/c_4.png
   :align:   center
   
Save file dialog:

.. figure::  images/c_5.png
   :align:   center

Salida por consola::

	msgbox: None
	inputbox: 
	confirmDialog: 0
	filechooser: D:\gvdata\countries027.geojson
	filechooser: [u'D:\\gvdata\\countries024.geojson', u'D:\\gvdata\\countries025.geojson', u'D:\\gvdata\\countries026.geojson',
				u'D:\\gvdata\\countries027.geojson', u'D:\\gvdata\\countries028.geojson', u'D:\\gvdata\\countries029.geojson',
				u'D:\\gvdata\\countries030.geojson']
	openFileDialog: [u'D:\\gvdata\\countries028.geojson']
	openFolderDialog: [u'D:\\gvdata\\GISofThrones\\GoTRelease']
	saveFileDialog: [u'D:\\gvdata\\newfile.shp']
