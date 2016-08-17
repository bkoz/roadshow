#** Lab 2: Smoke Test and Quick Tour **

###** Using the Command Line Interface (CLI)**

The first thing we want to do to ensure that the *oc* command line tool was installed and successfully added to our path is login to the OpenShift Enterprise 3.0 environment that has been provided for this Roadshow session.  In order to login, we will use the *oc* command and then specify the server that we want to authenticate to.  Issue the following command:

	$ oc login --username=openshift-dev --password=devel --server=10.1.2.2:8443
    
###**Creating a project**

Projects are a top level concept to help you organize your deployments. An
OpenShift project allows a community of users (or a user) to organize and manage
their content in isolation from other communities. Each project has its own
resources, policies (who can or cannot perform actions), and constraints (quotas
and limits on resources, etc).  Projects act as a "wrapper" around all the
application services and endpoints you (or your teams) are using for your work.
For this first lab, we are going to use a project named *userXX-smoke* that has been
created and populated with an application for you.

During this lab, we are going to use a few different commands to make sure that
things in the environment are working as expected.  Don't worry if you don't
understand all of the terminology as we will cover it in detail in later labs.

The first thing we want to do is switch to the *userXX-smoke* project. You
can do this with the following command:

	$ oc new-project smoke
   
You will see the following confirmation message:

	Now using project "smoke" on server "https://10.1.2.2:8443".

Create an OpenShift application from an existing container.

        $ oc new-app openshift/hello-openshift

Check to see that pod is running.

        $ oc get pods

You should see output similar to the following:

    NAME                      READY     STATUS    RESTARTS   AGE
    hello-openshift-1-ws01j   1/1       Running   0          58s

Look at the logs:

         $ oc logs hello-openshift-1-ws01j

Create a route by exposing the service:

         $ oc expose service hello-openshift
  
         route "hello-openshift" exposed

The next thing we want to check is the routes associated with this project. A simple explanation for how routes work is:
1. A request comes in to an OpenShift node on port 80 (HTTP) or 443 (HTTPS)
1. A Docker container running the router is bound to those ports, and receives the request
1. The router looks at the HTTP header for the host entry and matches it with a defined route
1. The router proxies the request on to a service endpoint that corresponds to that defined route

In order to view the routes for your project, enter in the following command:

         $ oc get route


You should see output similar to the following:
	
    NAME      HOST/PORT                                                     PATH      SERVICE   LABELS      TLS TERMINATION
    smoke     hello-openshift-smoke.rhel-cdk.10.1.2.2.xip.io                          smoke     app=smoke 

Now use **curl** or a web browser to visit the application URL:

         $ curl http://hello-openshift-smoke.rhel-cdk.10.1.2.2.xip.io

The following output should be reported:

         Hello OpenShift!

###**The Web Console**

OpenShift Enterprise 3 ships with a web-based console that will allow users to
perform various tasks via a browser.  To get a feel for how the web console
works, open your browser and go to the following URL:

	https://10.1.2.2:8443

Enter the same user name and password that you used with the CLI above.

![OpenShift 3 Login Screen](http://training.runcloudrun.com/images/roadshow/v3login.png)

After you have authenticated to the web console, you will be presented with a
list of projects that your user has permission to work with. You will see
something that looks like the following image:

![Web Console](http://training.runcloudrun.com/images/roadshow/webconsole1.png)

Click on the *userXX-smoke* project. When you click on the *userXX-smoke*
project, you will be taken to the project overview page which will list all of
the routes, services, deployments, and pods that you have running as part of
your project.  For this example, you will see a frontend that is deployed to
two pods.

![Web Console](http://training.runcloudrun.com/images/roadshow/webconsole2.png)

Once you have digested the information on the overview page, click on the Browse tab on the left hand side of the screen:

![Web Console](http://training.runcloudrun.com/images/roadshow/webconsole3.png)

Go ahead and play around a bit more with the web console to get familiar with
the various tabs and options.  However, we will be using the command line tools
for the majority of this lab.


**End of Lab 2**
