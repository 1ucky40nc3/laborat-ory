# An example RESTful API written in Rust


This is an example RESTful API written in Rust. The API implements the following endpoints:


| Endpoint               | Description                                                  |
|------------------------|--------------------------------------------------------------|
| /                      | The base path of the RESTful-API. This exposes a Swagger UI. |
| /admin                 | An admin endpoint that is supposed to be protected.          |
| /api-docs/openapi.json | The generated OpenAPI documentation of the REST-API.         |