# Spring-Boot Camel QuickStart

This example demonstrates how you can use Apache Camel with Spring Boot.

The quickstart uses Spring Boot to configure a little application that includes a Camel route that triggers a message every 5th second, and routes the message to a log.

### Building

The example can be built with

    mvn clean spring-boot:run

### Running the example in OpenShift

	
### Running the example in OpenShift
The example can be built and run on OpenShift using a single goal:

    mvn fabric8:deploy
    
When the example runs in OpenShift, you can use the OpenShift client tool to inspect the status

To list all the running pods:

    oc get pods

Then find the name of the pod that runs this quickstart, and output the logs from the running pods with:

    oc logs <name of pod>

You can also use the OpenShift [web console](https://docs.openshift.com/container-platform/3.3/getting_started/developers_console.html#developers-console-video) to manage the
running pods, and view logs and much more.

### Running via an S2I Application Template

Application templates allow you deploy applications to OpenShift by filling out a form in the OpenShift console that allows you to adjust deployment parameters.  This template uses an S2I source build so that it handle building and deploying the application for you.

First, import the Fuse image streams:

    oc create -f https://raw.githubusercontent.com/jboss-fuse/application-templates/GA/fis-image-streams.json

Then create the quickstart template:

    oc create -f https://raw.githubusercontent.com/jboss-fuse/application-templates/GA/quickstarts/spring-boot-camel-template.json

Now when you use "Add to Project" button in the OpenShift console, you should see a template for this quickstart. 



### CURL TEST:

	curl http://127.0.0.1:8082/api/api-docs

	curl http://127.0.0.1:8082/api/itemQuery

	curl http://127.0.0.1:8082/api/itemQuery/123

	curl -d "@data.json" -H "Content-Type: application/json" -X POST http://127.0.0.1:8082/api/itemQuery

### data.json
	
	{
    	"name": "test",
    	"description": "765483921",
    	"number": "2",
    	"itemNo": "0000",
    	"made": ""
	}
