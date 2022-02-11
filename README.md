# Jenkins Docker Image with Pre-Install Plugin

## Using Jenkins Base image

1. Create Dockerfile

   ```Dockerfile
   FROM jenkins/jenkins
   ```

2. build docker image with tag/latest

   ```shell
   docker build . -t bomb0069/jenkins:0.0.1 -t bomb0069/jenkins
   ```

3. Run Jenkins

    ```shell
    $ docker run bomb0069/jenkins

    Running from: /usr/share/jenkins/jenkins.war
    webroot: EnvVars.masterEnvVars.get("JENKINS_HOME")
    2022-02-11 19:52:15.115+0000 [id=1]     INFO    org.eclipse.jetty.util.log.Log#initialized: Logging initialized @283ms to org.eclipse.jetty.util.log.JavaUtilLog
    2022-02-11 19:52:15.152+0000 [id=1]     INFO    winstone.Logger#logInternal: Beginning extraction from war file
    2022-02-11 19:52:15.664+0000 [id=1]     WARNING o.e.j.s.handler.ContextHandler#setContextPath: Empty contextPath
    2022-02-11 19:52:15.706+0000 [id=1]     INFO    org.eclipse.jetty.server.Server#doStart: jetty-9.4.43.v20210629; built: 2021-06-30T11:07:22.254Z; git: 526006ecfa3af7f1a27ef3a288e2bef7ea9dd7e8; jvm 11.0.14+9
    2022-02-11 19:52:15.843+0000 [id=1]     INFO    o.e.j.w.StandardDescriptorProcessor#visitServlet: NO JSP Support for /, did not find org.eclipse.jetty.jsp.JettyJspServlet
    2022-02-11 19:52:15.878+0000 [id=1]     INFO    o.e.j.s.s.DefaultSessionIdManager#doStart: DefaultSessionIdManager workerName=node0
    2022-02-11 19:52:15.878+0000 [id=1]     INFO    o.e.j.s.s.DefaultSessionIdManager#doStart: No SessionScavenger set, using defaults
    2022-02-11 19:52:15.879+0000 [id=1]     INFO    o.e.j.server.session.HouseKeeper#startScavenging: node0 Scavenging every 600000ms
    2022-02-11 19:52:16.116+0000 [id=1]     INFO    hudson.WebAppMain#contextInitialized: Jenkins home directory: /var/jenkins_home found at: EnvVars.masterEnvVars.get("JENKINS_HOME")
    2022-02-11 19:52:16.249+0000 [id=1]     INFO    o.e.j.s.handler.ContextHandler#doStart: Started w.@338cc75f{Jenkins v2.334,/,file:///var/jenkins_home/war/,AVAILABLE}{/var/jenkins_home/war}
    2022-02-11 19:52:16.264+0000 [id=1]     INFO    o.e.j.server.AbstractConnector#doStart: Started ServerConnector@3a3e78f{HTTP/1.1, (http/1.1)}{0.0.0.0:8080}
    2022-02-11 19:52:16.264+0000 [id=1]     INFO    org.eclipse.jetty.server.Server#doStart: Started @1433ms
    2022-02-11 19:52:16.266+0000 [id=24]    INFO    winstone.Logger#logInternal: Winstone Servlet Engine running: controlPort=disabled
    2022-02-11 19:52:16.417+0000 [id=31]    INFO    jenkins.InitReactorRunner$1#onAttained: Started initialization
    2022-02-11 19:52:16.431+0000 [id=29]    INFO    jenkins.InitReactorRunner$1#onAttained: Listed all plugins
    2022-02-11 19:52:16.824+0000 [id=29]    INFO    jenkins.InitReactorRunner$1#onAttained: Prepared all plugins
    2022-02-11 19:52:16.827+0000 [id=37]    INFO    jenkins.InitReactorRunner$1#onAttained: Started all plugins
    2022-02-11 19:52:16.833+0000 [id=32]    INFO    jenkins.InitReactorRunner$1#onAttained: Augmented all extensions
    2022-02-11 19:52:17.131+0000 [id=31]    INFO    jenkins.InitReactorRunner$1#onAttained: System config loaded
    2022-02-11 19:52:17.131+0000 [id=30]    INFO    jenkins.InitReactorRunner$1#onAttained: System config adapted
    2022-02-11 19:52:17.131+0000 [id=30]    INFO    jenkins.InitReactorRunner$1#onAttained: Loaded all jobs
    2022-02-11 19:52:17.132+0000 [id=30]    INFO    jenkins.InitReactorRunner$1#onAttained: Configuration for all jobs updated
    2022-02-11 19:52:17.145+0000 [id=51]    INFO    hudson.model.AsyncPeriodicWork#lambda$doRun$1: Started Download metadata
    2022-02-11 19:52:17.150+0000 [id=51]    INFO    hudson.util.Retrier#start: Attempt #1 to do the action check updates server
    WARNING: An illegal reflective access operation has occurred
    WARNING: Illegal reflective access by org.codehaus.groovy.reflection.CachedClass (file:/var/jenkins_home/war/WEB-INF/lib/groovy-all-2.4.21.jar) to method java.lang.Object.finalize()
    WARNING: Please consider reporting this to the maintainers of org.codehaus.groovy.reflection.CachedClass
    WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
    WARNING: All illegal access operations will be denied in a future release
    2022-02-11 19:52:17.381+0000 [id=38]    INFO    jenkins.install.SetupWizard#init: 

    *************************************************************
    *************************************************************
    *************************************************************

    Jenkins initial setup is required. An admin user has been created and a password generated.
    Please use the following password to proceed to installation:

    15b28058954b423c8dbdff633d4b6b01

    This may also be found at: /var/jenkins_home/secrets/initialAdminPassword

    *************************************************************
    *************************************************************
    *************************************************************
    ```

## Disabling the Steup Wizard

```Dockerfile
FROM jenkins/jenkins:latest
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
```

```shell
$ docker run --rm -p 8080:8080 bomb0069/jenkins


Running from: /usr/share/jenkins/jenkins.war
webroot: EnvVars.masterEnvVars.get("JENKINS_HOME")
2022-02-11 19:59:25.177+0000 [id=1]     INFO    org.eclipse.jetty.util.log.Log#initialized: Logging initialized @278ms to org.eclipse.jetty.util.log.JavaUtilLog
2022-02-11 19:59:25.216+0000 [id=1]     INFO    winstone.Logger#logInternal: Beginning extraction from war file
2022-02-11 19:59:25.721+0000 [id=1]     WARNING o.e.j.s.handler.ContextHandler#setContextPath: Empty contextPath
2022-02-11 19:59:25.751+0000 [id=1]     INFO    org.eclipse.jetty.server.Server#doStart: jetty-9.4.43.v20210629; built: 2021-06-30T11:07:22.254Z; git: 526006ecfa3af7f1a27ef3a288e2bef7ea9dd7e8; jvm 11.0.14+9
2022-02-11 19:59:25.884+0000 [id=1]     INFO    o.e.j.w.StandardDescriptorProcessor#visitServlet: NO JSP Support for /, did not find org.eclipse.jetty.jsp.JettyJspServlet
2022-02-11 19:59:25.911+0000 [id=1]     INFO    o.e.j.s.s.DefaultSessionIdManager#doStart: DefaultSessionIdManager workerName=node0
2022-02-11 19:59:25.911+0000 [id=1]     INFO    o.e.j.s.s.DefaultSessionIdManager#doStart: No SessionScavenger set, using defaults
2022-02-11 19:59:25.912+0000 [id=1]     INFO    o.e.j.server.session.HouseKeeper#startScavenging: node0 Scavenging every 660000ms
2022-02-11 19:59:26.152+0000 [id=1]     INFO    hudson.WebAppMain#contextInitialized: Jenkins home directory: /var/jenkins_home found at: EnvVars.masterEnvVars.get("JENKINS_HOME")
2022-02-11 19:59:26.271+0000 [id=1]     INFO    o.e.j.s.handler.ContextHandler#doStart: Started w.@338cc75f{Jenkins v2.334,/,file:///var/jenkins_home/war/,AVAILABLE}{/var/jenkins_home/war}
2022-02-11 19:59:26.287+0000 [id=1]     INFO    o.e.j.server.AbstractConnector#doStart: Started ServerConnector@3a3e78f{HTTP/1.1, (http/1.1)}{0.0.0.0:8080}
2022-02-11 19:59:26.287+0000 [id=1]     INFO    org.eclipse.jetty.server.Server#doStart: Started @1389ms
2022-02-11 19:59:26.288+0000 [id=24]    INFO    winstone.Logger#logInternal: Winstone Servlet Engine running: controlPort=disabled
2022-02-11 19:59:26.443+0000 [id=31]    INFO    jenkins.InitReactorRunner$1#onAttained: Started initialization
2022-02-11 19:59:26.461+0000 [id=32]    INFO    jenkins.InitReactorRunner$1#onAttained: Listed all plugins
2022-02-11 19:59:26.874+0000 [id=32]    INFO    jenkins.InitReactorRunner$1#onAttained: Prepared all plugins
2022-02-11 19:59:26.876+0000 [id=29]    INFO    jenkins.InitReactorRunner$1#onAttained: Started all plugins
2022-02-11 19:59:26.879+0000 [id=34]    INFO    jenkins.InitReactorRunner$1#onAttained: Augmented all extensions
2022-02-11 19:59:27.172+0000 [id=30]    INFO    jenkins.InitReactorRunner$1#onAttained: System config loaded
2022-02-11 19:59:27.173+0000 [id=30]    INFO    jenkins.InitReactorRunner$1#onAttained: System config adapted
2022-02-11 19:59:27.173+0000 [id=30]    INFO    jenkins.InitReactorRunner$1#onAttained: Loaded all jobs
2022-02-11 19:59:27.174+0000 [id=30]    INFO    jenkins.InitReactorRunner$1#onAttained: Configuration for all jobs updated
2022-02-11 19:59:27.190+0000 [id=51]    INFO    hudson.model.AsyncPeriodicWork#lambda$doRun$1: Started Download metadata
2022-02-11 19:59:27.195+0000 [id=51]    INFO    hudson.util.Retrier#start: Attempt #1 to do the action check updates server
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.codehaus.groovy.reflection.CachedClass (file:/var/jenkins_home/war/WEB-INF/lib/groovy-all-2.4.21.jar) to method java.lang.Object.finalize()
WARNING: Please consider reporting this to the maintainers of org.codehaus.groovy.reflection.CachedClass
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
2022-02-11 19:59:27.301+0000 [id=37]    INFO    jenkins.InitReactorRunner$1#onAttained: Completed initialization
2022-02-11 19:59:27.363+0000 [id=23]    INFO    hudson.lifecycle.Lifecycle#onReady: Jenkins is fully up and running
```

## Installing Jenkins Plugins

plugins.txt

```txt
robot
golang
```

```Dockerfile
FROM jenkins/jenkins:latest

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt
```

```shell
docker build . -t bomb0069/jenkins:0.0.1 -t bomb0069/jenkins
```

```shell
docker run --rm -p 8080:8080 bomb0069/jenkins