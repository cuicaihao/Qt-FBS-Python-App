# Create Qt Application (Exe) with Qt5/PySide2 with FBS

This tutorial shows how you can use fbs to create a simple Python GUI and an associated installer:

You can follow this tutorial on Windows, Mac or Linux. You need Python 3.5-3.8.

## Setup

### Method A
Create a virtual environment in the current directory:
```bash
python3 -m venv venv
```
Activate the virtual environment:
```bash
# On Mac/Linux:
source venv/bin/activate
# On Windows:
call venv\scripts\activate.bat
```
### Method B 
Or you can use `conda` to create a virtual environment
```bash
conda create -n pyQt python=3.8
```
The remainder of the tutorial assumes that the virtual environment is active.

Install the required libraries (most notably, fbs and PyQt5):

```bash
pip install fbs==0.9.0
pip install PyQt5==5.15.2
pip install PySide2==5.15.2
pip install pyinstaller==4.3
```
**Note: fbs the latest version is not free, so here we use its early version. You may see there is warning about the fbs on pyinstaller, which says fbs needs pyinstaller=3.4, just ignore it.**

## Run the app
To run the basic PyQt application from source, execute the following command:
```bash
fbs run
```
This shows a (admittedly not very exciting) window. 

![app_GUI](images\app_gui.png)

![app_GUI](images\app_gui_clickbutton.png)

![app_GUI](images\app_gui_clickbutton_ii.png)


## Freezing the app
We want to turn the source code of our app into a standalone executable that can be run on your users' computers. In the context of Python applications, this process is called "freezing".

Use the following command to turn the app's source code into a standalone executable:

```bash
fbs freeze
```

This creates the folder target/Tutorial. You can copy this directory to any other computer (with the same OS as yours) and run the app there! Isn't that awesome?

## Creating an installer
Desktop applications are normally distributed by means of an installer. On Windows, this would be an executable called TutorialSetup.exe. On Mac, mountable disk images such as Tutorial.dmg are commonly used. On Linux, .deb files are common on Ubuntu, .rpm on Fedora / CentOS, and .pkg.tar.xz on Arch.

fbs lets you generate each of the above packages via the command:
```bash
fbs installer
```
Depending on your operating system, this may require you to first install some tools. Please read on for OS-specific instructions.

## Windows installer
Before you can use the installer command on Windows, please install [NSIS](http://nsis.sourceforge.net/Main_Page) and add its installation directory to your PATH environment variable.

The installer is created at `target/HelloSetup.exe`. It lets your users pick the installation directory and adds your app to the Start Menu. It also creates an entry in Windows' list of installed programs. Your users can use this to uninstall your app. The following screenshots show these steps in action:


![app_GUI](images\Installer_A.png)

![app_GUI](images\Installer_B.png)

![app_GUI](images\Installer_C.png)

![app_GUI](images\Installer_D.png)

## Summary
fbs lets you use Python and Qt to create desktop applications for Windows, Mac and Linux. It can create installers for your app, and automatically handles the packaging of third-party libraries and data files. These things normally take weeks to figure out. fbs gives them to you in minutes instead.

## Comments
This demo can be easily transformed into other application with the Qt Creator and Studio.

## References
- [QT for Python](https://www.qt.io/qt-for-python)
- [fbs tutorial](https://github.com/mherrmann/fbs-tutorial)
