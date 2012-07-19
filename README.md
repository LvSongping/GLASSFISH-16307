GLASSFISH-16307
===============

I deploy my app 'web25.war' using the CUI. Later I deploy another app 'WEB25.war'. No errors in console or server log, but I noticed domains\domain1\applications only has a directory WEB25, no web25.
I undeploy 'web25', again seemingly successful. But when I then try to disable WEB25 I get an error:

D:\GFv3.1\glassfish-3.1\glassfish3\glassfish>bin\asadmin disable
Enter the value for the name operand> WEB25
remote failure:
Command disable failed.

In server.log an NPE:

[#|2011-04-03T11:41:31.796+1000|SEVERE|glassfish3.1|javax.enterprise.system.tools.admin.org.glassfish.deployment.admin|_ThreadID=56;_ThreadName=Thread-1;|Error during disabling: 
java.lang.NullPointerException
at com.sun.enterprise.deploy.shared.FileArchive.getDirectories(FileArchive.java:175)
at org.glassfish.deployment.common.DeploymentUtils.isEARFromIntrospecting(DeploymentUtils.java:332)
at org.glassfish.deployment.common.DeploymentUtils.isEAR(DeploymentUtils.java:320)
at org.glassfish.javaee.full.deployment.EarHandler.handles(EarHandler.java:146)
[...]
[#|2011-04-03T11:42:22.218+1000|WARNING|glassfish3.1|javax.enterprise.system.tools.admin.org.glassfish.deployment.admin|_ThreadID=82;_ThreadName=Thread-1;|Cannot find application bits at D:\tests\GFv3.1\glassfish-3.1\glassfish3\glassfish\domains\domain1\applications\WEB25|#]

If deployment of apps only differing in case is not supported it would be better not to allow it.


 

