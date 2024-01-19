# What is 10.10.0?

10.10.0 is an approach to building enterprise apps based on [Golang](https://go.dev) and [HTMX](https://htmx.org) that enables the [rapid](what/develop.md) development of [evergreen](what/evergreen.md) and [zero ops](what/zero.md) apps.

[Golang](https://go.dev) is used for frontend and backend development because of its backward compatibility guarantee, meaning code that is written today will compile ten years from now (as has been the case for that last ten years).

10.10.0 apps have almost no dependencies (direct and indirect) which means these apps have minimal supply chain issues such as obsolescence, patching, etc. The few dependences that are used have been stable for many years.

10.10.0 apps use technologies pioneered in **digital natives**, but are tailored to meet the
requirements and complexities found in **enterprise**. Specifically:

- Trade-off in favour of simplicity over very high throughput requirements of digital natives
- Trade-off simplicity in favour of more operational and security controls
