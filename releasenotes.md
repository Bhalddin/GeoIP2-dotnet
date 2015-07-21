GeoIP2 .NET API Release Notes
=============================

2.3.1 (2015-07-21)
------------------

* Upgrade to MaxMind.Db 1.1.0.
* Fix serialization on exceptions.

2.3.1-beta1 (2015-06-30)
------------------------

* Upgrade to Json.NET 7.0.1.
* Upgrade to MaxMind.Db 1.1.0-beta1. This release includes a number of
  significant improvements for the memory-mapped file mode.

2.3.0 (2015-06-29)
------------------

* `AverageIncome` and `PopulationDensity` were added to the `Location`
  model for use with the new fields in GeoIP2 Insights.
* `IsAnonymousProxy` and `IsSatelliteProvider` in `GeoIP2.Model.Traits` have
  been deprecated. Please use our [GeoIP2 Anonymous IP
  database](https://www.maxmind.com/en/geoip2-anonymous- ip-database) to
  determine whether an IP address is used by an anonymizing service.

2.2.0 (2015-05-19)
------------------

* All of the database methods in `DatabaseReader` and all of the web service
  methods in `WebServiceClient` now have a counterpart that takes an
  `IPAddress` instead of a `string`. Pull request by Guillaume Turri. GitHub
  #24.
* The `JsonIgnore` attribute was added to `Names` in `NamedEntity` and
  `Subdivisions` in `AbstractCityResponse` as  these were already exposed to
  JSON.NET through the private field backing them. Pull request by Dan Byrne
  GitHub #21.
* The interfaces `IGeoIP2DatabaseReader` and `IGeoIP2WebServicesClient` were
  added to facilitate dependency injection and mocking. Pull request by Naz
  Soogund. GitHub #22.
* A `HasCoordinates` getter was added to the `Location` class. This will
  return true if both the `Latitude` and `Longitude` have values. Pull request
  by Darren Hickling. GitHub #23.
* All of the response and model properties now set the appropriate
  `JsonProperty` rather than relying an JSON.NET's automatic matching.
  Serializing these objects should now product JSON much more similar to the
  JSON returned by the web service and internal structure of the data in
  database files.
* Dependencies were updated to most recent versions.

2.1.0 (2014-11-06)
------------------

* Added support for the GeoIP2 Anonymous IP database. The `DatabaseReader`
  class now has an `AnonymousIP()` method which returns an
  `AnonymousIpResponse` object.

2.0.0 (2014-09-29)
------------------

* First production release.

0.5.0 (2014-09-24)
------------------

* The deprecated `CityIspOrg` and `Omni` methods were removed.
* `DatabaseReader` methods will now throw an `InvalidOperationException` when
  called for the wrong database type.
* `DatabaseReader` now has a `Metadata` property that provides an object
   containing the metadata for the open database.

0.4.0 (2014-07-22)
------------------

* The web service client API has been updated for the v2.1 release of the web
  service. In particular, the `CityIspOrg` and `Omni` methods on
  `WebServiceClient` have been deprecated. The `City` method now provides all
  of the data formerly provided by `CityIspOrg`, and the `Omni` method has
  been replaced by the `Insights` method.
* Support was added for the GeoIP2 Connection Type, Domain, and ISP databases.


0.3.3 (2014-06-02)
------------------

* Constructors with named parameters were added to the model and response
  classes. (Jon Wynveen)

0.3.2 (2014-04-09)
------------------

* A constructor taking a `Stream` was added to `DatabaseReader`.
* Fixed dependency on wrong version of `Newtonsoft.Json`.

0.3.1 (2014-02-13)
------------------

* Fixed broken error handling. Previously the wrong exceptions and error
  messages were returned for some web service errors.

0.3.0 (2013-11-15)
------------------

* API CHANGE: Renamed exceptions to remove GeoIP2 prefixes.
* Improved error messages when RestSharp does not return an HTTP status code.

0.2.0 (2013-10-25)
------------------

* First release with GeoIP2 database support. See `DatabaseReader` class.

0.1.1 (2013-10-04)
------------------

* Build documentation.

0.1.0 (2013-09-20)
------------------

* Initial release.