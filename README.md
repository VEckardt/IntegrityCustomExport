# IntegrityCustomExport
The CustomExport is a customized solution to enhance the Integrity Gateway.

## Purpose
This is the base enhancement for the Integrity Gateway. It adds additional functionality to the Gateway to retrieve, for example, related items from Integity to add these to the output stream for your MS Word report.

![CustomExport](doc/CustomExport.PNG)

## Use Cases
- Create a Test Session Report with Defect and Test Objective details. 

## Install
In IntegrityClient folder
- Put the "IntegrityClient/IntegrityCustomGateway.jar" directly into your own IntegrityClient folder
- Copy also the files "IntegrityClient/lib/IntegrityAPI.jar" and "IntegrityClient/lib/jfxmessagebox-1.1.0.jar" into your IntegrityClient/lib folder
- Add a custom menu entry with:
```
name: Custom Export
program:  ../jre/bin/javaw.exe
parameter: -jar ../IntegrityCustomGateway.jar
```
- Add the following type proprty to your Test Session type
```
name: Gateway.Configurations
value:  Test Protocol,Test Protocol
description: (Custom) The names of the export configurations for the selected type
```
- Merge "IntegrityClient\bin\add-to-Gateway.lax.txt" into your own "bin\Gateway.lax"
- Merge "IntegrityClient\config\gateway\add-to-gateway-tool-config.txt" into your own "config\gateway\gateway-tool-configuration.xml"
- Copy all remaining content from "IntegrityClient\config" into your own "config"
- Create a field "Is Meaningful" (type=logical, calculation="IsMeaningful()") and add it to your "Test" type 

## How to test
- Select a Test Session
- click Custom > Custom Export
- The custom form should open
- Start the Gateway with a click at the [Generate] button
- Then review the outcome

## Hints
- Update the Layout to fulfill your individual needs.
- If more attributes should be extracted, adapt/update the mapping file
- Keep in mind that the Mapping File Structure is a specific configuration for this Mulit-Type extract!

## Move to Server
- You can move all the local files (except lax and libs) onto your Integrity Server.
- Distribute the jar files and the lax file to other Integrity client installations.
- Configure a ViewSet with the Custom Menu entry and share it.

##  Development environment
- PTC Integrity LM 10.9 (also 11.0 is fine)
- Netbeans 7.4 (or 8)
- Java 1.7 (or 1.8)

## Known Limitations
- none
