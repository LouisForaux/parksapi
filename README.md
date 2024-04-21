# ThemeParks.wiki Parks API

[![Unit Test](https://github.com/ThemeParks/parksapi/actions/workflows/unit_test.js.yml/badge.svg)](https://github.com/ThemeParks/parksapi/actions/workflows/unit_test.js.yml) [![pages-build-deployment](https://github.com/ThemeParks/parksapi/actions/workflows/pages/pages-build-deployment/badge.svg)](https://github.com/ThemeParks/parksapi/actions/workflows/pages/pages-build-deployment)

[API Documentation](https://themeparks.github.io/parksapi/)

This is a backend module to fetch and query live data for themeparks. This source code powers the free-to-use API at [ThemeParks.wiki](https://themeparks.wiki)

To fetch data from the API, you should look at the client libraries:
* https://github.com/ThemeParks/ThemeParks_JavaScript
* https://github.com/ThemeParks/ThemeParks_Python

Fetching and parsing logic is provided in this source code. Most parks require some form of credentials, which are not supplied in this repo. You will need to source these yourself.

General support is available for the ThemeParks.wiki API, and not this source code (except for Sponsors with support benefits).

`test.js` contains a basic set of sanity checks and output validation, which also shows how a destination object can be accessed.

Each destination generates *entities*. Entities can be of various types:

* Destinations
  * i.e, Resorts
  * These are not called resorts to avoid confusion for parks that are not part of resorts
  * eg. Walt Disney World Resort
* Parks
  * All parks must be within a Destination entity
  * eg. Magic Kingdom
* Attraction
  * A ride / transport / etc.
  * Attraction entities must be within a Destination entity (usually also within a park, but not always)
  * eg. Pirates of the Carribean
* Resturant
  * A dining location within a destination
  * eg. Casey's Corner
* Show
  * A show / parade entity with scheduled show times
  * eg. Main Street Electrical Parade

*Entity Types Being Finalised - Destinations, Parks, and Attractions however, are well supported and unlikely to change*

## Adding Destinations

Best current documentation for this is to check out `scripts/templateDestination.js` and look at the existing supported destinations.

Setup `index.js` with your new class, and edit `test.js` to test your destination to check everything is setup correctly.

## Destinations

<!-- BEGIN_DESTINATIONS -->
* WaltDisneyWorldResort
* DisneylandResort
* DisneylandParis
* TokyoDisneyResort
* HongKongDisneyland
* ShanghaiDisneylandResort
* UniversalStudios
* UniversalOrlando
* EuropaPark
* Efteling
* Phantasialand
* SeaworldOrlando
* SeaworldSanAntonio
* SeaworldSanDiego
* BuschGardensTampa
* BuschGardensWilliamsburg
* AltonTowers
* ThorpePark
* ChessingtonWorldOfAdventures
* LegolandWindsor
* LegolandOrlando
* LegolandCalifornia
* LegolandBillund
* LegolandDeutschland
* Gardaland
* PortAventuraWorld
* ParcAsterix
* Toverland
* Dollywood
* SilverDollarCity
* Plopsaland
* HolidayPark
* Bellewaerde
* WalibiHolland
* HeidePark
* Liseberg
* CedarPoint
* KnottsBerryFarm
* CaliforniasGreatAmerica
* CanadasWonderland
* Carowinds
* KingsIsland
* DorneyPark
* KingsDominion
* MichigansAdventure
* ValleyFair
* WorldsOfFun
* Hersheypark
* SixFlags
* HansaPark
<!-- END_DESTINATIONS -->

## Configuration

Destination objects can be configured by either passing an object of variables into the constructor, or using environment variables (the preferred way).

To use environment variables, create a file called `.env` in the working directory of your project.

Environment variables are structured as:
* Class name (upper case)
* Underscore _
* Variable name (upper case)

For example, the class `WaltDisneyWorldResort` has a `resortId` configuration variable which can be loaded through the environment variable `WALTDISNEYWORLDRESORT_RESORTID`

Some classes expose "parent scopes" to allow configuring environment variables once for a range of destinations. For example, Attractions.io's base URL can be configured once through `ATTRACTIONSIO_BASEURL` rather than configuring it identically for every destination.

Environment Variables (auto-generated):

<!-- BEGIN_ENV -->
```
WALTDISNEYWORLDRESORT_RESORTID
WALTDISNEYWORLDRESORT_RESORTSHORTCODE
WALTDISNEYWORLDRESORT_PARKIDS
WALTDISNEYWORLDRESORT_VIRTUALQUEUEURL
WALTDISNEYWORLDRESORT_GENIEDATA
WALTDISNEYWORLDRESORT_SLUG
DISNEYLANDRESORT_RESORTID
DISNEYLANDRESORT_RESORTSHORTCODE
DISNEYLANDRESORT_PARKIDS
DISNEYLANDRESORT_VIRTUALQUEUEURL
DISNEYLANDRESORT_GENIEDATA
DISNEYLANDRESORT_SLUG
DISNEYLANDPARIS_APIKEY
DISNEYLANDPARIS_APIBASE
DISNEYLANDPARIS_APIBASEWAITTIMES
DISNEYLANDPARIS_LANGUAGE
DISNEYLANDPARIS_STANDBYAPIBASE
DISNEYLANDPARIS_STANDBYAPIKEY
DISNEYLANDPARIS_STANDBYAUTHURL
DISNEYLANDPARIS_STANDBYAPIREFRESHTOKEN
DISNEYLANDPARIS_PREMIERACCESSAPIKEY
DISNEYLANDPARIS_PREMIERACCESSURL
DISNEYLANDPARIS_USERAGENT
TOKYODISNEYRESORT_APIKEY
TOKYODISNEYRESORT_APIAUTH
TOKYODISNEYRESORT_APIOS
TOKYODISNEYRESORT_APIBASE
TOKYODISNEYRESORT_APIVERSION
TOKYODISNEYRESORT_PARKIDS
TOKYODISNEYRESORT_FALLBACKDEVICEID
HONGKONGDISNEYLAND_RESORTID
HONGKONGDISNEYLAND_DESTINATIONID
HONGKONGDISNEYLAND_RESORTSHORTCODE
HONGKONGDISNEYLAND_CULTUREFILTER
HONGKONGDISNEYLAND_PARKIDS
HONGKONGDISNEYLAND_SLUG
HONGKONGDISNEYLAND_VIRTUALQUEUEURL
HONGKONGDISNEYLAND_GENIEDATA
SHANGHAIDISNEYLANDRESORT_APIBASE
SHANGHAIDISNEYLANDRESORT_APIAUTH
SHANGHAIDISNEYLANDRESORT_PARKIDS
UNIVERSALSTUDIOS_CITY
UNIVERSALSTUDIOS_RESORTSLUG
UNIVERSALSTUDIOS_RESORTKEY
UNIVERSALSTUDIOS_SECRETKEY
UNIVERSALSTUDIOS_APPKEY
UNIVERSALSTUDIOS_VQUEUEURL
UNIVERSALSTUDIOS_BASEURL
UNIVERSALSTUDIOS_ASSETSBASE
UNIVERSALORLANDO_CITY
UNIVERSALORLANDO_RESORTSLUG
UNIVERSALORLANDO_RESORTKEY
UNIVERSALORLANDO_SECRETKEY
UNIVERSALORLANDO_APPKEY
UNIVERSALORLANDO_VQUEUEURL
UNIVERSALORLANDO_BASEURL
UNIVERSALORLANDO_ASSETSBASE
EUROPAPARK_PARKS
EFTELING_APIKEY
EFTELING_APIVERSION
EFTELING_APPVERSION
EFTELING_SEARCHURL
EFTELING_WAITTIMESURL
PHANTASIALAND_APIBASE
SEAWORLDORLANDO_RESORTIDS
SEAWORLDORLANDO_RESORTID
SEAWORLDORLANDO_RESORTSLUG
SEAWORLDORLANDO_APPID
SEAWORLDORLANDO_APPVERSION
SEAWORLDORLANDO_BASEURL
SEAWORLDSANANTONIO_RESORTIDS
SEAWORLDSANANTONIO_RESORTID
SEAWORLDSANANTONIO_RESORTSLUG
SEAWORLDSANANTONIO_APPID
SEAWORLDSANANTONIO_APPVERSION
SEAWORLDSANANTONIO_BASEURL
SEAWORLDSANDIEGO_RESORTIDS
SEAWORLDSANDIEGO_RESORTID
SEAWORLDSANDIEGO_RESORTSLUG
SEAWORLDSANDIEGO_APPID
SEAWORLDSANDIEGO_APPVERSION
SEAWORLDSANDIEGO_BASEURL
BUSCHGARDENSTAMPA_RESORTIDS
BUSCHGARDENSTAMPA_RESORTID
BUSCHGARDENSTAMPA_RESORTSLUG
BUSCHGARDENSTAMPA_APPID
BUSCHGARDENSTAMPA_APPVERSION
BUSCHGARDENSTAMPA_BASEURL
BUSCHGARDENSWILLIAMSBURG_RESORTIDS
BUSCHGARDENSWILLIAMSBURG_RESORTID
BUSCHGARDENSWILLIAMSBURG_RESORTSLUG
BUSCHGARDENSWILLIAMSBURG_APPID
BUSCHGARDENSWILLIAMSBURG_APPVERSION
BUSCHGARDENSWILLIAMSBURG_BASEURL
ALTONTOWERS_DESTINATIONID
ALTONTOWERS_PARKID
ALTONTOWERS_INITIALDATAVERSION
ALTONTOWERS_APPBUILD
ALTONTOWERS_APPVERSION
ALTONTOWERS_BASEURL
ALTONTOWERS_DEVICEIDENTIFIER
ALTONTOWERS_APIKEY
ALTONTOWERS_CALENDARURL
THORPEPARK_DESTINATIONID
THORPEPARK_PARKID
THORPEPARK_INITIALDATAVERSION
THORPEPARK_APPBUILD
THORPEPARK_APPVERSION
THORPEPARK_BASEURL
THORPEPARK_DEVICEIDENTIFIER
THORPEPARK_APIKEY
THORPEPARK_CALENDARURL
CHESSINGTONWORLDOFADVENTURES_DESTINATIONID
CHESSINGTONWORLDOFADVENTURES_PARKID
CHESSINGTONWORLDOFADVENTURES_INITIALDATAVERSION
CHESSINGTONWORLDOFADVENTURES_APPBUILD
CHESSINGTONWORLDOFADVENTURES_APPVERSION
CHESSINGTONWORLDOFADVENTURES_BASEURL
CHESSINGTONWORLDOFADVENTURES_DEVICEIDENTIFIER
CHESSINGTONWORLDOFADVENTURES_APIKEY
CHESSINGTONWORLDOFADVENTURES_CALENDARURL
LEGOLANDWINDSOR_DESTINATIONID
LEGOLANDWINDSOR_PARKID
LEGOLANDWINDSOR_INITIALDATAVERSION
LEGOLANDWINDSOR_APPBUILD
LEGOLANDWINDSOR_APPVERSION
LEGOLANDWINDSOR_BASEURL
LEGOLANDWINDSOR_DEVICEIDENTIFIER
LEGOLANDWINDSOR_APIKEY
LEGOLANDWINDSOR_CALENDARURL
LEGOLANDORLANDO_DESTINATIONID
LEGOLANDORLANDO_PARKID
LEGOLANDORLANDO_INITIALDATAVERSION
LEGOLANDORLANDO_APPBUILD
LEGOLANDORLANDO_APPVERSION
LEGOLANDORLANDO_BASEURL
LEGOLANDORLANDO_DEVICEIDENTIFIER
LEGOLANDORLANDO_APIKEY
LEGOLANDORLANDO_CALENDARURL
LEGOLANDCALIFORNIA_DESTINATIONID
LEGOLANDCALIFORNIA_PARKID
LEGOLANDCALIFORNIA_INITIALDATAVERSION
LEGOLANDCALIFORNIA_APPBUILD
LEGOLANDCALIFORNIA_APPVERSION
LEGOLANDCALIFORNIA_BASEURL
LEGOLANDCALIFORNIA_DEVICEIDENTIFIER
LEGOLANDCALIFORNIA_APIKEY
LEGOLANDCALIFORNIA_CALENDARURL
LEGOLANDBILLUND_DESTINATIONID
LEGOLANDBILLUND_PARKID
LEGOLANDBILLUND_INITIALDATAVERSION
LEGOLANDBILLUND_APPBUILD
LEGOLANDBILLUND_APPVERSION
LEGOLANDBILLUND_BASEURL
LEGOLANDBILLUND_DEVICEIDENTIFIER
LEGOLANDBILLUND_APIKEY
LEGOLANDBILLUND_CALENDARURL
LEGOLANDDEUTSCHLAND_DESTINATIONID
LEGOLANDDEUTSCHLAND_PARKID
LEGOLANDDEUTSCHLAND_INITIALDATAVERSION
LEGOLANDDEUTSCHLAND_APPBUILD
LEGOLANDDEUTSCHLAND_APPVERSION
LEGOLANDDEUTSCHLAND_BASEURL
LEGOLANDDEUTSCHLAND_DEVICEIDENTIFIER
LEGOLANDDEUTSCHLAND_APIKEY
LEGOLANDDEUTSCHLAND_CALENDARURL
GARDALAND_DESTINATIONID
GARDALAND_PARKID
GARDALAND_INITIALDATAVERSION
GARDALAND_APPBUILD
GARDALAND_APPVERSION
GARDALAND_BASEURL
GARDALAND_DEVICEIDENTIFIER
GARDALAND_APIKEY
GARDALAND_CALENDARURL
PORTAVENTURAWORLD_APIBASE
PORTAVENTURAWORLD_GUESTUSERNAME
PORTAVENTURAWORLD_GUESTPASSWORD
PORTAVENTURAWORLD_WAITTIMEURL
PARCASTERIX_APIBASE
PARCASTERIX_LANGUAGE
TOVERLAND_APIBASE
TOVERLAND_CALENDARURL
TOVERLAND_AUTHTOKEN
TOVERLAND_LANGUAGES
DOLLYWOOD_DESTINATIONID
DOLLYWOOD_DESTINATIONSLUG
DOLLYWOOD_CRMBASEURL
DOLLYWOOD_CRMGUID
DOLLYWOOD_CRMATTRACTIONSID
DOLLYWOOD_CRMDININGID
DOLLYWOOD_CRMSHOWID
DOLLYWOOD_APIBASE
DOLLYWOOD_CRMAUTH
SILVERDOLLARCITY_DESTINATIONID
SILVERDOLLARCITY_DESTINATIONSLUG
SILVERDOLLARCITY_CRMBASEURL
SILVERDOLLARCITY_CRMGUID
SILVERDOLLARCITY_CRMATTRACTIONSID
SILVERDOLLARCITY_CRMDININGID
SILVERDOLLARCITY_CRMSHOWID
SILVERDOLLARCITY_APIBASE
SILVERDOLLARCITY_CRMAUTH
PLOPSALAND_DESTINATIONSLUG
PLOPSALAND_PARKSLUG
PLOPSALAND_BASEURL
PLOPSALAND_BASELANG
PLOPSALAND_CLIENTID
PLOPSALAND_CLIENTSECRET
HOLIDAYPARK_DESTINATIONSLUG
HOLIDAYPARK_PARKSLUG
HOLIDAYPARK_BASEURL
HOLIDAYPARK_BASELANG
HOLIDAYPARK_CLIENTID
HOLIDAYPARK_CLIENTSECRET
BELLEWAERDE_DESTINATIONSLUG
BELLEWAERDE_PARKID
BELLEWAERDE_BASEURL
BELLEWAERDE_REALTIMEURL
WALIBIHOLLAND_DESTINATIONSLUG
WALIBIHOLLAND_PARKID
WALIBIHOLLAND_BASEURL
WALIBIHOLLAND_REALTIMEURL
HEIDEPARK_DESTINATIONID
HEIDEPARK_PARKID
HEIDEPARK_INITIALDATAVERSION
HEIDEPARK_APPBUILD
HEIDEPARK_APPVERSION
HEIDEPARK_BASEURL
HEIDEPARK_DEVICEIDENTIFIER
HEIDEPARK_APIKEY
HEIDEPARK_CALENDARURL
LISEBERG_RESORTID
LISEBERG_BASEURL
CEDARPOINT_PARKID
CEDARPOINT_DESTINATIONID
CEDARPOINT_BASEURL
CEDARPOINT_REALTIMEBASEURL
CEDARPOINT_CONFIGPATH
CEDARPOINT_LONGITUDE
CEDARPOINT_LATITUDE
CEDARPOINT_EXTRAATTRACTIONCATEGORYTYPES
CEDARPOINT_EXTRASHOWCATEGORYTYPES
CEDARPOINT_EXTRARESTAURANTCATEGORYTYPES
CEDARPOINT_ATTRACTIONCATEGORIES
CEDARPOINT_SHOWCATEGORIES
CEDARPOINT_DININGCATEGORIES
KNOTTSBERRYFARM_PARKID
KNOTTSBERRYFARM_DESTINATIONID
KNOTTSBERRYFARM_EXTRAATTRACTIONCATEGORYTYPES
KNOTTSBERRYFARM_BASEURL
KNOTTSBERRYFARM_REALTIMEBASEURL
KNOTTSBERRYFARM_CONFIGPATH
KNOTTSBERRYFARM_LONGITUDE
KNOTTSBERRYFARM_LATITUDE
KNOTTSBERRYFARM_EXTRASHOWCATEGORYTYPES
KNOTTSBERRYFARM_EXTRARESTAURANTCATEGORYTYPES
KNOTTSBERRYFARM_ATTRACTIONCATEGORIES
KNOTTSBERRYFARM_SHOWCATEGORIES
KNOTTSBERRYFARM_DININGCATEGORIES
CALIFORNIASGREATAMERICA_PARKID
CALIFORNIASGREATAMERICA_DESTINATIONID
CALIFORNIASGREATAMERICA_BASEURL
CALIFORNIASGREATAMERICA_REALTIMEBASEURL
CALIFORNIASGREATAMERICA_CONFIGPATH
CALIFORNIASGREATAMERICA_LONGITUDE
CALIFORNIASGREATAMERICA_LATITUDE
CALIFORNIASGREATAMERICA_EXTRAATTRACTIONCATEGORYTYPES
CALIFORNIASGREATAMERICA_EXTRASHOWCATEGORYTYPES
CALIFORNIASGREATAMERICA_EXTRARESTAURANTCATEGORYTYPES
CALIFORNIASGREATAMERICA_ATTRACTIONCATEGORIES
CALIFORNIASGREATAMERICA_SHOWCATEGORIES
CALIFORNIASGREATAMERICA_DININGCATEGORIES
CANADASWONDERLAND_PARKID
CANADASWONDERLAND_DESTINATIONID
CANADASWONDERLAND_BASEURL
CANADASWONDERLAND_REALTIMEBASEURL
CANADASWONDERLAND_CONFIGPATH
CANADASWONDERLAND_LONGITUDE
CANADASWONDERLAND_LATITUDE
CANADASWONDERLAND_EXTRAATTRACTIONCATEGORYTYPES
CANADASWONDERLAND_EXTRASHOWCATEGORYTYPES
CANADASWONDERLAND_EXTRARESTAURANTCATEGORYTYPES
CANADASWONDERLAND_ATTRACTIONCATEGORIES
CANADASWONDERLAND_SHOWCATEGORIES
CANADASWONDERLAND_DININGCATEGORIES
CAROWINDS_PARKID
CAROWINDS_DESTINATIONID
CAROWINDS_BASEURL
CAROWINDS_REALTIMEBASEURL
CAROWINDS_CONFIGPATH
CAROWINDS_LONGITUDE
CAROWINDS_LATITUDE
CAROWINDS_EXTRAATTRACTIONCATEGORYTYPES
CAROWINDS_EXTRASHOWCATEGORYTYPES
CAROWINDS_EXTRARESTAURANTCATEGORYTYPES
CAROWINDS_ATTRACTIONCATEGORIES
CAROWINDS_SHOWCATEGORIES
CAROWINDS_DININGCATEGORIES
KINGSISLAND_PARKID
KINGSISLAND_DESTINATIONID
KINGSISLAND_BASEURL
KINGSISLAND_REALTIMEBASEURL
KINGSISLAND_CONFIGPATH
KINGSISLAND_LONGITUDE
KINGSISLAND_LATITUDE
KINGSISLAND_EXTRAATTRACTIONCATEGORYTYPES
KINGSISLAND_EXTRASHOWCATEGORYTYPES
KINGSISLAND_EXTRARESTAURANTCATEGORYTYPES
KINGSISLAND_ATTRACTIONCATEGORIES
KINGSISLAND_SHOWCATEGORIES
KINGSISLAND_DININGCATEGORIES
DORNEYPARK_VENUEID
DORNEYPARK_DESTINATIONID
DORNEYPARK_SUBDOMAIN
DORNEYPARK_APIDOMAIN
DORNEYPARK_APIUSER
DORNEYPARK_APIPASS
DORNEYPARK_RIDETYPES
DORNEYPARK_DININGTYPES
KINGSDOMINION_PARKID
KINGSDOMINION_DESTINATIONID
KINGSDOMINION_CONFIGPATH
KINGSDOMINION_BASEURL
KINGSDOMINION_REALTIMEBASEURL
KINGSDOMINION_LONGITUDE
KINGSDOMINION_LATITUDE
KINGSDOMINION_EXTRAATTRACTIONCATEGORYTYPES
KINGSDOMINION_EXTRASHOWCATEGORYTYPES
KINGSDOMINION_EXTRARESTAURANTCATEGORYTYPES
KINGSDOMINION_ATTRACTIONCATEGORIES
KINGSDOMINION_SHOWCATEGORIES
KINGSDOMINION_DININGCATEGORIES
MICHIGANSADVENTURE_PARKID
MICHIGANSADVENTURE_DESTINATIONID
MICHIGANSADVENTURE_CONFIGPATH
MICHIGANSADVENTURE_BASEURL
MICHIGANSADVENTURE_REALTIMEBASEURL
MICHIGANSADVENTURE_LONGITUDE
MICHIGANSADVENTURE_LATITUDE
MICHIGANSADVENTURE_EXTRAATTRACTIONCATEGORYTYPES
MICHIGANSADVENTURE_EXTRASHOWCATEGORYTYPES
MICHIGANSADVENTURE_EXTRARESTAURANTCATEGORYTYPES
MICHIGANSADVENTURE_ATTRACTIONCATEGORIES
MICHIGANSADVENTURE_SHOWCATEGORIES
MICHIGANSADVENTURE_DININGCATEGORIES
VALLEYFAIR_VENUEID
VALLEYFAIR_DESTINATIONID
VALLEYFAIR_SUBDOMAIN
VALLEYFAIR_APIDOMAIN
VALLEYFAIR_APIUSER
VALLEYFAIR_APIPASS
VALLEYFAIR_RIDETYPES
VALLEYFAIR_DININGTYPES
WORLDSOFFUN_PARKID
WORLDSOFFUN_DESTINATIONID
WORLDSOFFUN_CONFIGPATH
WORLDSOFFUN_BASEURL
WORLDSOFFUN_REALTIMEBASEURL
WORLDSOFFUN_LONGITUDE
WORLDSOFFUN_LATITUDE
WORLDSOFFUN_EXTRAATTRACTIONCATEGORYTYPES
WORLDSOFFUN_EXTRASHOWCATEGORYTYPES
WORLDSOFFUN_EXTRARESTAURANTCATEGORYTYPES
WORLDSOFFUN_ATTRACTIONCATEGORIES
WORLDSOFFUN_SHOWCATEGORIES
WORLDSOFFUN_DININGCATEGORIES
HERSHEYPARK_APIKEY
HERSHEYPARK_BASEURL
SIXFLAGS_BASEURL
SIXFLAGS_AUTHHEADER
HANSAPARK_RESORTID
HANSAPARK_BASEURL
HANSAPARK_LOCALE
HANSAPARK_APIKEY
```
<!-- END_ENV -->