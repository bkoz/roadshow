#** Lab 1: Installing the OpenShift CLI **

###**Command Line Interface**

OpenShift 3 ships with a feature rich web console as well as command line tools to provide users with a nice interface to work with applications deployed to the platform.  The OpenShift CLI tool is a single executable (*oc*) written in the Go programming language and is available for the following operating systems:

- Microsoft Windows
- Apple OS X
- Linux

####**Downloading the CLI tool**

Download the correct executable for your operating system as linked below:

- [Microsoft Windows](http://presto.haveopen.com/~bkozdemb/workshop/oc-clients/windows/oc.exe)
- [Apple OS X](http://presto.haveopen.com/~bkozdemb/workshop/oc-clients/macosx/oc)
- [Linux](http://presto.haveopen.com/~bkozdemb/workshop/oc-clients/linux/oc)


Once the *oc* file has been download, copy it to a directory of your choosing then add that directory to your PATH environment variable. 

####**Adding *oc* to your PATH environment variable**

**Windows:**
Because changing your PATH on windows varies by version of the operating system, we will not list each operating system here.  However, the general workflow is right click on your computer name inside of the file explorer.  Select Advanced system settings. I guess changing your PATH is considered an advanced task? :) Click on the advanced tab, and then finally click on Environment variables.  Once the new dialog opens, select the Path variable and add ";C:\OpenShift" at the end.  For an easy way out, you could always just copy it to C:\Windows or a directory you know is already on your path. For more detailed instructions:



[Windows XP](https://support.microsoft.com/en-us/kb/310519)

[Windows Vista](http://banagale.com/changing-your-system-path-in-windows-vista.htm)

[Windows 7](http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx "Windows 7")

[Windows 8](http://www.itechtics.com/customize-windows-environment-variables/)

Windows 10 - Follow the directions above.

**OS X:**

	$ export PATH=$PATH:~/OpenShift

**Linux:**
	
	$ export PATH=$PATH:~/OpenShift


####**Verify**
At this point, we should have the oc tool available for use.  Let's test this out by printing the version of the oc command:

	$ oc version

You should see the following:

    oc v3.2.1.9-1-g2265530
    kubernetes v1.2.0-36-g4a3f9c5

If you get an error message, you have not updated your path correctly.  If you need help, raise your hand and the instructor will assist.



**End of Lab 1**
