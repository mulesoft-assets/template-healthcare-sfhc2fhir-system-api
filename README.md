# Template Healthcare Salesforce Health Cloud to FHIR System API

Underlying all IT architectures are core systems of records that are often not readily available due to its complexity and connectivity concerns. System APIs provide a means of hiding that complexity from the user while exposing data and providing downstream insulation from any interface changes or rationalization of those systems. This API provides an implementation best practice to expose data from patient management systems like Salesforce Health Cloud via a set of RESTful FHIR services in RAML 1.0, making it easy to consume within an enterprise.

![](https://www.lucidchart.com/publicSegments/view/6c0eab9d-b684-43bd-96c5-61b323fd6399/image.png)

## License Agreement

Using this template is subject to the conditions of this <a href="https://github.com/mulesoft/template-sfdc2nets-opportunity-aggregation/blob/4.1/AnypointTemplateLicense.pdf">License Agreement</a>. Review the terms of the license before downloading and using this template. In short, you are allowed to use the template for free with Mule Enterprise Edition, CloudHub, or as a trial in Anypoint Studio.

## Catalyst Accelerator for Healthcare

This FHIR specification is one of many components included in [Catalyst Accelerator for Healthcare](/exchange/68ef9520-24e9-4cf2-b2f5-620025690913/catalyst-accelerator-for-healthcare/). It provides organizations with connectivity assets that accelerate project delivery in healthcare, including pre-built API designs and implementations that support core healthcare business processes. 

# Use Case

As a user of Healthcare API Led Connectivity Web Portal I want a microservice to act as a system API to provide services to upper layers of the architecture. This include creation, modification and retrieval of medical data from the Salesforce Health Cloud system.

Salesforce Health Cloud to FHIR System API is part of the Healthcare Templates Solution and uses the standardized FHIR structures [version 3.0.1 STU3](https://www.hl7.org/FHIR/index.html).

The API is defined using RAML 1.0 to provide type information for validation of requests and to help with the data transformation during development by providing useful metadata.

The following FHIR objects and operations are implemented in this API:

- **AllergyIntolerance** - read, update, create
- **Appointment** - read, update, create
- **Condition** - read, update, create
- **Device** - read, update, create
- **MedicationOrder** - create
- **Observation** - read, create
- **Patient** - read, update, create
- **Practitioner** - read, update, create

# Considerations

To make this template run, there are certain preconditions that must be considered. Failing to do so can lead to unexpected behavior of the template.

# Run it!
Simple steps to get this template running.

## Where to Download Anypoint Studio and the Mule Runtime

If you are new to Mule, download this software:

- [Download Anypoint Studio](https://www.mulesoft.com/platform/studio)
- [Download Mule runtime](https://www.mulesoft.com/lp/dl/mule-esb-enterprise)

## Import an Anypoint Template into Studio

In Studio, click the Exchange X icon in the upper left of the taskbar, log in with your Anypoint Platform credentials, search for the template, and click **Open**.

## Run on Studio
After you have import your template into Anypoint Studio, follow these steps to run it:

1. Locate the properties file `mule.dev.properties`, in src/main/resources.
2. Complete all the properties required per the examples in the "Properties to Configure" section.
3. Right click the template project folder.
4. Hover your mouse over `Run as`.
5. Click `Mule Application (configure)`.
6. Inside the dialog, select Environment and set the variable `mule.env` to the value `dev`.
7. Click `Run`.

## Run on Mule Stand Alone

Fill in the properties in one of the property files, for example in mule.prod.properties and run your app with the corresponding environment variable to use it. To follow the example, use `mule.env=prod`.

## Run on CloudHub

If creating your application on CloudHub, go to Manage Application > Properties to set all environment variables detailed in "Properties to Configure".

### Deploy Your Template on CloudHub

In Studio, right click your project name in Package Explorer and select
Anypoint Platform > Deploy on CloudHub.

## Properties to Configure

To use this template you need to configure the properties that follow either in a properties file or in CloudHub as environment variables. 

### Application Properties

- http.port `8081`

### SalesForce Connector Configuration

- sfdc.username `example@email.com`
- sfdc.password `sfdcPassword`
- sfdc.token `12345dfnsjad54s54da54w5d4a5`
