
##Bac Kan LUCM draft results

These are the Windows+MinGW commands, convert them to linux is trivial

###Load these resources in geostore

* Open a terminal and set these variables with the proper values 
* Note that PROV_ID is set to the Bac Kan id since these resources are related only to that province

```
set SERVER_DOMAIN=the host name/ip es:redd.vnforest.gov.vn
set USER=admin username
set PSWD=admin password
set RESOURCES_PATH=The absolute path on FS of the directory where the files to load are stored
set PROV_ID=6
```

* Then copy and paste these **cUrl** requests, they are self-explanatory

```
curl -u %USER%:%PSWD% -XPOST -H "Content-type: text/xml" -d @%RESOURCES_PATH%prov%PROV_ID%_1995-2015.xml http://%SERVER_DOMAIN%/diss_geostore/rest/resources
curl -u %USER%:%PSWD% -XPOST -H "Content-type: text/xml" -d @%RESOURCES_PATH%prov%PROV_ID%_2000-2015.xml http://%SERVER_DOMAIN%/diss_geostore/rest/resources
curl -u %USER%:%PSWD% -XPOST -H "Content-type: text/xml" -d @%RESOURCES_PATH%prov%PROV_ID%_2005-2015.xml http://%SERVER_DOMAIN%/diss_geostore/rest/resources
curl -u %USER%:%PSWD% -XPOST -H "Content-type: text/xml" -d @%RESOURCES_PATH%prov%PROV_ID%_1010-2015.xml http://%SERVER_DOMAIN%/diss_geostore/rest/resources
```

Each request, if it's successfully terminated, returns the id of the resource inserted.

* To display all the available resources: `http://redd.vnforest.gov.vn/diss_geostore/rest/resources/`
* To display a single resource: `http://redd.vnforest.gov.vn/diss_geostore/rest/resources/resource/$ID`
* To delete a single resource: `curl -u %USER%:%PSWD% -XDELETE -H "Content-type: text/xml" http://%SERVER_DOMAIN%/diss_geostore/rest/resources/resource/$ID`
* To display a single resource as a json add the HTTP header ``Accept: application/json`` (so no browser, use postman, poster or curl)