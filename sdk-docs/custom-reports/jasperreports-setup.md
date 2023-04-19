---
title: JasperReports setup
category: 61fcd8e1a448f5004215317c
parentDocSlug: custom-reports
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

To start developing new custom reports you need to get a development environment setup. Following all of these sections should get you up and running.

## Jaspersoft Studio
Install the latest version of Jaspersoft Studio from https://community.jaspersoft.com/project/jaspersoft-studio/releases

## Webservice Data Source
To be able to access our GraphQL API from Jaspersoft Studio you will need the Webservice Datasource plug-in found "here".

1. Open the folder [Webservice Datasource plug-in directory]\JSS
2. Copy the .jar files in this folder
3. Open the folder [Jaspersoft Studio Installation directory]\plugins and paste the previously copied .jars

## Trackunit plugin for JasperReports
For authorization of the GraphQL queries we are using a bearer token header. To make scheduling work and to make it easier to develop reports in Jaspersoft Studio we have developed a utility plugin. You need to add it as a dependency to your project in Jaspersoft Studio:
1. Get the latest version of the tu-jasperreports-utils.jar from Trackunit
2. Right click the project and select Properties
3. Go to Java Build Path – Projects (Tab)
4. Click Add... and navigate to and select the .jar file

## JasperReports development server
For testing the custom reports you can use our development environment and our JasperReports development server.

After adding the server to Jaspersoft Studio you can upload the report designs and test them in the Reports section of Trackunit Manager.

Follow these steps to add the JasperReports development  server to your Jaspersoft Studio:

1. Go to the Repository Explorer tab and right click the Servers section and create a
new connection

1. Fill out the dialog with the URL https://jasperreports.dev.awsapi.trackunit.com/jasperserver/ and the username and password that has been provided by Trackunit

You should now have a connection to the Trackunit Development Report Server and you should be ready to design your first report.