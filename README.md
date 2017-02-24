* [Initial article](https://spring.io/guides/gs/centralized-configuration/)
* [Initial article repo](https://github.com/spring-guides/gs-centralized-configuration.git)
* [Spring Cloud Config docs](Spring Cloud Config Server)

Both server and client and SpringBoot apps. Server is using git-repository on file system.
Configuration files in that repository should have the same names, as client applications.

# Table of content
* [Server](#Server)
* [How to run](#How to run)

## Server <a name="Server"/>

## How to run <a name="How to run"/>
* Make sure that correct path to git repository with client configuration is specified in
 configuration-service\src\main\resources\application.properties
 For Win file:/// should be used as prefixe, for other systems file://. Also on Win everything
 is working without prefix at all.
```
spring.cloud.config.server.git.uri=file:///D:/work/Examples/@springconfig/config
```
* Make sure that in git repo with configurations file with the same name as application name of client, configured
in configuration-client\src\main\resources\bootstrap.properties
```
spring.application.name=a-bootiful-client
```
In related git project with configurations there is file a-bootiful-client.properties. This file must contain
property that will be used by client and MUST be committed.
* Run server

Run from CLI or just from IDEA configurations from configurations-service folder.
```
mvn spring-boot:run
```
* Run client
Run from CLI or just from IDEA configurations from configurations-client folder.
```
mvn spring-boot:run
```
* Access client controller.
```
http://localhost:8080/message
```
If everything is working and property is extracted from file - we should see [Hello world]. If something goes
wrong - we should see [Hello default]
