API v0 Documentation
====================

Please note that this is an early development version of the API. This version is liable to break or change at any time,
so we do not recommended using it for any production purposes. Additionally, this documentation is being used as a specification during development, so not all functionality described here is necessarily implemented. Please [let us know](mailto:magicbus@umich.edu?subject=API Feedback) if you have any feedback.

Known Issues which will be resolved before the v1 release:
* Arrivals method not yet implemented
* Does not pretty print by default
* Does not necessarily return complete or accurate data

Future Considerations:
* will require developers to register with their email to receive an authentication token. This will enable us to track usage and contact developers regarding update and deprecation schedules.
* will hopefully return gzip'd responses
* will possibly use CORS instead of JSONP


## Format

### Requests

The API uses only RESTful HTTP GET methods. The standard format for a request is:
`GET http://mbus.pts.umich.edu/api/<version>/<resource>/`
Where:
* `<version>` is the API version you want to use. Currently `v0` is the only option.
* `<resource>` is the type of data you want to receive, such as `routes`, `buses`, `stops`, etc.

See below for specifics on each method.

### Responses

The API returns JSON-encoded objects with the 'Content-Type: application/json' header.

All requests are JSONP enabled. To use JSONP, append `callback=your_callback` to the query string of the request. For example, to retrieve a JSONP response with the routes data: `GET http://mbus.pts.umich.edu/api/v0/routes/?callback=process_routes`


## Resources

- [**<code>GET</code>  /api/v0/announcements/**](https://github.com/magic-bus/api-documentation/blob/master/resources/announcements.md)
- [**<code>GET</code>  /api/v0/arrivals/**](https://github.com/magic-bus/api-documentation/blob/master/resources/arrivals.md)
- [**<code>GET</code>  /api/v0/buses/**](https://github.com/magic-bus/api-documentation/blob/master/resources/buses.md)
- [**<code>GET</code>  /api/v0/routes/**](https://github.com/magic-bus/api-documentation/blob/master/resources/routes.md)
- [**<code>GET</code>  /api/v0/stops/**](https://github.com/magic-bus/api-documentation/blob/master/resources/stops.md)


## Contributions

While designing the Magic Bus API and its documentation, we looked for help and inspiration from other well-designed APIs.

* [Kippt](https://github.com/kippt/api-documentation)
* [Tumblr](http://www.tumblr.com/docs/en/api/v2)

## Authors

[Thomas Lovett](http://tklovett.com/)