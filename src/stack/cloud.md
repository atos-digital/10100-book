# Cloud

- terraform
- make

Cloud sdks are used to interact with infrastructure such as databases, pub/sub, etc.

- (optional) [Docker](https://www.docker.com/) for building of the app container image and local running of components such as databases
- (optional) Relevant cloud sdk from AWS, Azure or GCP

##  Azure

Microsoft Azure have some very useful features that can be used to create a microservices platform with zero ops.
[Dapr architecture](https://learn.microsoft.com/en-us/azure/architecture/example-scenario/serverless/microservices-with-container-apps-dapr) is a good example of this.
We can simplify this further by using only ACI and Dapr where needed.

```mermaid
C4Context
      title Simple microservices platform
      System_Ext(Users, "Internet", "Users")
      Boundary(az, "Azure", "Cloud") {
            System(gateway, "Load balancer", "Azure Load Balancer")
            Boundary(srvvpc, "Services", "VPC") {
                  System(microserviceA, "DAPR Microservice", "10100 App")
                  System(microserviceB, "DAPR Microservice", "10100 App")
                  System(microserviceC, "DAPR Microservice", "10100 App")
                  System(microserviceD, "DAPR Microservice", "10100 App")

                  Boundary(dapr, "Events", "PubSub") {
                        SystemQueue(pubsub, "PubSub", "DAPR managed")
                  }
            }

            Boundary(db, "Data", "VPC") {
                  SystemDb(SystemE, "Database", "App data")
            }
      }

```
