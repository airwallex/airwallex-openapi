# Airwallex OpenAPI

Canonical, versioned, machine-readable OpenAPI specifications for the
[Airwallex](https://www.airwallex.com) Client API.

## OpenAPI version

The specs are **OpenAPI 3.1.0**. Make sure your tooling supports 3.1 (which
aligns the schema model with JSON Schema 2020-12). Most modern generators and
viewers — `openapi-generator`, Redocly, Swagger UI, Postman, Bruno — do.

## API versioning

Airwallex uses **date-based API versioning**. Each published version in this
repo corresponds to a version date such as `2026-08-21`.

Select a version at request time with the **`x-api-version`** header:

```
x-api-version: 2026-08-21
```

- Pin the `x-api-version` value your integration was built and tested against so
  behaviour stays stable as new versions are released.
- The folder you generate an SDK from should match the `x-api-version` you send.
- Omitting the header falls back to your account's default version; pinning is
  strongly recommended for production integrations.

## Base URLs

| Environment        | Base URL                          |
| ------------------ | --------------------------------- |
| Production         | `https://api.airwallex.com`       |
| Demo (sandbox)     | `https://api-demo.airwallex.com`  |

Build and test against the demo environment before switching to production.

## Vendor extensions

Beyond standard OpenAPI, the public spec carries a small set of extensions useful to external consumers.

| Field                    | Level                         | Meaning                                                             |
| ------------------------ | ----------------------------- | ------------------------------------------------------------------- |
| `x-resourceLevel`        | operation                     | Resource / authorization level the operation applies at (e.g. `account`, `org`). |
| `x-oauthSupported`       | operation                     | Whether the operation supports OAuth (boolean).                     |
| `x-enumDescriptions`     | schema                        | Per-enum-value descriptions (value → explanation).                  |
| `x-examples`             | operation                     | Example requests and responses (including request `uri` and headers). |
| `examples` (native OAS)  | request/response + parameters | Example requests and responses.                                     |
| `x-badges`               | tag / operation               | Beta / Alpha / Deprecated badges.                                   |
| `x-displayName`          | tag                           | Human-friendly resource names.                                      |
| `x-tagGroups`            | root                          | Groups tags by API domain for navigation.                           |

## Documentation

- API reference: <https://www.airwallex.com/docs/api>
- Developer docs: <https://www.airwallex.com/docs>

Spotted a problem with the spec or the API? [Open an
issue](https://github.com/airwallex/openapi/issues) — we triage them here and
work internally with the owning teams to address them. For account-specific or
urgent support, use the official support channels linked from the docs site. See
[CONTRIBUTING.md](./CONTRIBUTING.md) for details.

## License

Released under the [MIT License](./LICENSE).
