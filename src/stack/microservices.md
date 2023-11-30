# Microservices platform

- terraform or bicep
- make

We use terraform or bicep (for Azure) to create infrastructure as code to deploy the following
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
