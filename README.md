# RIPA
California Racial and Identity Profiling Act [(RIPA - AB953)](https://oag.ca.gov/ab953/regulations)

The San Diego County Sheriff's Department is developing this application to share and collaborate with the California L.E. community at large.

The RIPA App is a mobile first web application for phones and MDCs to capture stop information directly in the field. It is completely stand-alone and has no third party system integrations.

## Feature Highlight

* Semi offline
  * Cached lookups
  * Stop in progress
* Templates
* Pull forward on multiples
* Reverse geocoding
* Instrumentation
* Dark Mode
* Regulation reference links
* JSON documents

## Requirements

The application is built using MSFT ASP.NET MVC/WEBAPI with Entity Foundation and ReactJS views. 

* IIS (SSL is recommended)
* SQL Server 2016
* Visual Studio 
* Windows Authentication

## How To Get Started

**Database Setup** - On the package manager console in VS, add a new migration `add-migration myMigration` and update the database `update-database`, which you will need to point to in the web.config file. Alternatively, if you don't want to mess with migrations, you can implement the SQL script in the SQL folder.

The SQL folder also has a script for the lookup tables, along with sample data. It is recommended that you set up a repeatable process to update the lookup tables from California DoJ directly.

**IIS Setup** - Set up a new web application, turn on Windows Authentication and set up your port 443/https bindings, a dev cert will suffice, unless you are setting up production. Make sure the application pool identity has read/write access to the database you set up in the previous step.

**Update Web.config** - Make sure you update the app settings in Web.config with your agency specific information.
* `<add key="reverseGeoURI" value="https://www.mysite.us/arcgis/rest/....."/>`
* `<add key="agency" value="AG"/>`
* `<add key="ori" value="CA0000000"/>`
* `<add key="forceCacheUpdate" value="false" />`
* `<add key="allowedBackDateHours" value="24" />`
* `<add key="expireCacheDays" value="14" />`
* `<add key="useBeats" value="0" />` 0 = Don't use beats, 1 = Show beats, 2 = Make beats mandatory


