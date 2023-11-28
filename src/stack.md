# The 10.10.0 Tech Stack

This chapter describes the technology stack used in 10.10.0 applicattions and explains the reasons
for the technology choices. Take note of how few dependencies there are in this stack.

## Fronmtend
- golang
- htmx (https://htmx.org)
- tmpl (https://pkg.go.dev/text/template)
- make

Frontends are written in golang and served by the golang http server. Htmx is used for AJAX, CSS Transitions, 
WebSockets and Server Sent Events directly in HTML.

We do not use the node ecosystem due to its level of instability.

## Backend
- golang
- HTTP APIs
- standard lib (https://pkg.go.dev/std)
- cloud sdk
- make

Backends are written in golang and served by the golang http server. APIs are HTTP based and business logic is
dependent on standard lib only. Cloud sdks are used to interact with infrastructure such as databases, pub/sub, etc.

## Microservices platform
- terraform or bicept
- make

We use terraform or bicept (for Azure) to create infrastructure as code to deploy the following
microservice platform.

```
   |-----------------------------------------------------|
   |                  Https Load Balancer                |     // Https ingress to the platform
   |-----------------------------------------------------|
         |                              |
         |                 |------------------------|
         |                 |       API Gateway      |          // API gateway to support discovery, auth, etc
         |                 |------------------------|
         |                              |
         |           |----------| |----------| |----------|
         |           |   NEG    | |    NEG   | |    NEG   |     // Load balancing across kube clusters and data centres
         |           |----------| |----------| |----------|
         |                 |            |            |
   |-----------|     |----------| |----------| |----------|
   | public    |     | private  | | Frontend | | backend  |    // Only ingress from NEG
   | file      |     | file     | | web      | | API      |    // Various container services 
   | proxy     |     | proxy    | | server   | | services |    // Only egress to private network
   |-----------|     |----------| |----------| |----------|
         |                     |                 |
  |-------------|       |-------------|   |-------------|    |---------|
  |   Storage   |       |   Storage   |   |   private   |----| Jumpbox |  // VPN jumpbox
  |   (public)  |       |  (private)  |   |   network   |    |---------|
  |-------------|       |-------------|   |-------------|----VPC peering  // VPC peering IP
                                                 |
                                 |-------------|    |-------------|
                                 |   Database  |    |    Other    |
                                 |  (private)  |    |  (private)  |
                                 |-------------|    |-------------|

```

## CICD
- github actions

## Using Vision
We use a templating tool [Vision](https://github.com/vision-cli/vision) to produce the scaffolding code that
contains our best practice. It is not necessary to use this tool, Vision is not a dependency, but rather used as 
an accelerator.

For example:

Create a project which includes CICD code with:
```
vision project create myproject
```

Add a service to your project with:
```
cd myproject
vision service create myservice
```

Add the microservice platform code (for Azure in this example):
```
vision infra create azure
make infra
```