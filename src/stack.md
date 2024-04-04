# The 10.10.0 Tech Stack

This chapter describes the technology stack used in 10.10.0 applications and explains the reasons for their selection.

The stack's application is based on [Golang](https://go.dev). This provides a number of advantages:

- Backward compatibility. This is described in Go's website [here](https://go.dev/doc/go1compat) _"It is intended that programs written to the Go 1 specification will continue to compile and run correctly, unchanged, over the lifetime of that specification"_.

- No external linked libraries. Go code compiles into a self contained binary with no external dependencies such as .so or .dll libraries on the operating system. This has many benefits such as a reduced need for operations personnel and platforms teams. It does however require occasional recompile and deploy to ensure security vulnerabilites are fixed, but thanks to backward compatibility, this can be automated.

- Cloud native. Go was designed with fast compilation, startup and execution in mind. This makes Go apllications ideal for containerization and running in serverless cloud platforms. For example they can remain dormant (zero cost) and wake up within milliseconds to service a request when it comes in. Go applications are also multiplatform and can be compiled for any underlying infrastructure. All the cloud providers provide tooling and documention for automating go application containerization and deployment into their environments. Go provides a cloud efficient concurrency model, security model, and so on.

The stack's infra code is based on [Terraform](https://www.terraform.io). This provides a number of advantages:

- The code runs on all the cloud providers.

- Access to a large number of Terraform [modules](https://registry.terraform.io).
