# Template Healthcare SFHC to FHIR System API

+ [License Agreement](#licenseagreement)
+ [Use Case](#usecase)
+ [Considerations](#considerations)
	* [Cloudhub security considerations](#cloudhubsecurityconsiderations)
	* [APIs security considerations](#apissecurityconsiderations)
+ [Run it!](#runit)
	* [Running on premise](#runonopremise)
	* [Running on Studio](#runonstudio)
	* [Running on Mule ESB stand alone](#runonmuleesbstandalone)
	* [Running on CloudHub](#runoncloudhub)
	* [Deploying your Anypoint Template on CloudHub](#deployingyouranypointtemplateoncloudhub)
	* [Properties to be configured (With examples)](#propertiestobeconfigured)

# License Agreement <a name="licenseagreement"/>
Note that using this template is subject to the conditions of this [License Agreement](AnypointTemplateLicense.pdf).
Please review the terms of the license before downloading and using this template. In short, you are allowed to use the template for free with Mule ESB Enterprise Edition, CloudHub, or as a trial in Anypoint Studio.

# Use Case <a name="usecase"/>

TODO

This template should serve as a foundation for setting an API implementation for Condition data retrieval. API is defined in [RAML](https://docs.mulesoft.com/anypoint-platform-for-apis/walkthrough-design-existing#about-raml) and implementation is using [APIkit](https://docs.mulesoft.com/anypoint-platform-for-apis/apikit-basic-anatomy#basic-anatomy). Condition API is retrieving data from EHR system and transform them to JSON in respect with FHIR specification [version 1.0.2 DSTU2](https://www.hl7.org/FHIR/DSTU2/index.html). The solution should be secured, see the [API Security Consideration](#apissecurityconsiderations).

TODO

# Considerations <a name="considerations"/>

To make this Anypoint Template run, there are certain preconditions that must be considered. **Failling to do so could lead to unexpected behavior of the template.**

## Cloudhub security considerations <a name="cloudhubsecurityconsiderations"/>

+ When VPC is configured in a Cloudhub account, two additional **ports** are available **for internal calls: 8091 and 8092**
+ ${http.port} and ${https.port} are still reserved for external endpoints and should not be used for setting internal port values
+ Internal endpoints **can be configured using** proposed placeholders: **${http.internal.port}** and **${https.internal.port}**
+ There is a URL naming convention for **calls between applications within the same VPC: mule-worker-internal-<appname\>.cloudhub.io**
+ **Cloudhub will not replace provided SSL certificates for internal calls**, therefore they should be valid for the mentioned URL naming convention

## APIs security considerations <a name="apissecurityconsiderations"/>

### Expose internal endpoints with RAML and HTTPS
+ Blocking request - response processing strategy
+ Consumed internally by Salesforce Health Cloud to Experience API
+ Consumed externally by mobile apps (through HTTPS proxies with policies: basic auth, external OAuth2 provider, LDAP, etc)

### Consumes EHR web service
+ EHR instance within VPN (connected to Cloudhub account VPC)

# Run it! <a name="runit"/>
Simple steps to get Healthcare EHR to FHIR Condition Process API running.
See below.

## Running on premise <a name="runonopremise"/>
In this section we detail the way you should run your Anypoint Template on your computer.


### Where to Download Mule Studio and Mule ESB
First thing to know if you are a newcomer to Mule is where to get the tools.

+ You can download Mule Studio from this [Location](http://www.mulesoft.com/platform/mule-studio)
+ You can download Mule ESB from this [Location](http://www.mulesoft.com/platform/soa/mule-esb-open-source-esb)

### Importing an Anypoint Template into Studio
Mule Studio offers several ways to import a project into the workspace, for instance: 

+ Anypoint Studio generated Deployable Archive (.zip)
+ Anypoint Studio Project from External Location
+ Maven-based Mule Project from pom.xml
+ Mule ESB Configuration XML from External Location

You can find a detailed description on how to do so in this [Documentation Page](http://www.mulesoft.org/documentation/display/current/Importing+and+Exporting+in+Studio).

### Running on Studio <a name="runonstudio"/>
Once you have imported you Anypoint Template into Anypoint Studio you need to follow these steps to run it:

+ Generate keystore (You can find a detailed description on how to do so in this [Documentation Page](https://docs.mulesoft.com/mule-user-guide/v/3.7/tls-configuration#generating-keystores-and-truststores))
+ Locate the properties file `mule-app.properties`, in src/main/app
+ Complete all the properties required as per the examples in the section [Properties to be configured](#propertiestobeconfigured)
+ Once that is done, right click on you Anypoint Template project folder 
+ Hover you mouse over `"Run as"`
+ Click on  `"Mule Application"`

### Running on Mule ESB stand alone <a name="runonmuleesbstandalone"/>
Complete all properties in [mule-app.properties](../master/src/main/app/mule-app.properties) and run your app. 

## Running on CloudHub <a name="runoncloudhub"/>
While [creating your application on CloudHub](http://www.mulesoft.org/documentation/display/current/Hello+World+on+CloudHub) (Or you can do it later as a next step), you need to go to `"Manage Application"` > `"Properties"` to set all environment variables detailed in **Properties to be configured**.
Follow other steps defined [here](#runonpremise) and once your app is all set and started, there is no need to do anything else.

### Deploying your Anypoint Template on CloudHub <a name="deployingyouranypointtemplateoncloudhub"/>
Mule Studio provides you with really easy way to deploy your Template directly to CloudHub, for the specific steps to do so please check this [link](http://www.mulesoft.org/documentation/display/current/Deploying+Mule+Applications#DeployingMuleApplications-DeploytoCloudHub)

## Properties to be configured (With examples) <a name="propertiestobeconfigured"/>
In order to use this Mule Anypoint Template you need to configure properties (Credentials, configurations, etc.) either in properties file or in CloudHub as Environment Variables. Detail list with examples:
### Application properties

TODO