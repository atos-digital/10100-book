# Backend

Backends are written in golang and served by the golang http server. APIs are HTTP based and business logic is
dependent on standard lib only. Cloud sdks are used to interact with infrastructure such as databases, pub/sub, etc.

- [Golang standard lib](https://pkg.go.dev/std)
- [Make](https://www.gnu.org/software/make/) for simplicity
- (optional) [Docker](https://www.docker.com/) for building of the app container image and local running of components such as databases
- (optional) Relevant cloud sdk from AWS, Azure or GCP
