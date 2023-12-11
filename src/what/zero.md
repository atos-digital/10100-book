# Zero operations

## The status quo

Many enterprise IT systems today come with a significant maintenance burden, requiring teams to devote significant time to updating, upgrading, and patching applications as well as their third party dependencies. This takes up valuable developer time and reduces capacity for new feature development. In our view, there are two reasons for this.

### Tightly-coupled infrastructure and architecture

Large IT estates are diverse and often run on dedicated hardware, or if run in the cloud, on provisioned VMs to accommodate the different apps and standards built over the years. This tends to create a complex system of applications which rely on each other or on specific host configurations to work, making for a very inflexible and very fragile system - any part reaching its end of life or failing could lead to unpredictable chains of failure across the rest of the system. Time and resources must therefore be spent to maintain and troubleshoot the system just to keep it functioning, which adds little enduring value to the business. This traditional approach to IT infrastructure often results in high maintenance costs, extended downtimes, and increased risk of errors during updates or modifications. Additionally, the maintenance of such complex systems requires highly specialised knowledge usually vested in only a few individuals, creating the risk of a knowledge vacuum when these key persons leave the organisation.

### Lack of automation

A large amount of a developer’s valuable time is spent on what [Google calls “toil”](https://sre.google/sre-book/eliminating-toil/) – work that is manual, repetitive, automatable, and adds no enduring value. Toils can pervade all aspects of operations management, including deployment and release management, monitoring and logging, patching and upgrading, licence and certificate renewal, scaling, and disaster recovery. For instance, manual deployment processes require significant time investments from development and operations teams, increasing the likelihood of deployment errors leading to extended application downtime. Scaling infrastructure to accommodate varying workloads also becomes a manual headache, with developers dedicating significant time to provisioning and configuring resources.The cumulative effect is a strained development pipeline, hindered innovation, and increased operational costs as valuable human resources are diverted toward tasks that could be efficiently handled through automation.

## Our approach

### Managed services

Modern infrastructure is built around clearly containerised apps with well defined APIs. We believe teams should take advantage of managed cloud services which offer automated deployment, scaling, and management of containerized applications, removing the need for developers to perform mundane operational tasks. Additionally, isolating apps and their dependencies, and clearly defining their API boundaries, allows for them to be easily iterated on without causing breaking changes to the other apps that run alongside them.

### Culture shift

However, utilising these technologies is not sufficient - we believe that a culture of “zero-ops” must be embedded into the development process itself, with an emphasis on creating automated systems, checks, and CI/CD pipelines to reduce the need for a dedicated ops team and minimise the risk of human error. Tasks like the renewal of SSL certificates are not difficult to automate, yet are often left as manual chores for the operations team and forgotten about until they cause an issue. Developing apps with an emphasis on minimising manual maintenance and operations frees op teams up to focus on more valuable tasks like building new platforms, deploying new apps, and tuning performance and security, instead of mundane chores like rotating logs, adding storage, saving backups, planning maintenance windows, and so on.

By taking advantage of managed cloud services and adopting a “zero-ops” culture, we believe organisations can eliminate almost all of the maintenance tasks associated with applications and infrastructure.

<!-- This involves investing in automation to minimise and eliminate low value manual tasks toil in SRE terms. This includes toil in testing and deployment, day-to-day operations, scaling, and so on. The idea is that machines should do this toil.
Unfortunately a culture of cutting corners in enterprise has led to under-investment in automation
and armies of low value engineers keeping the lights on. Zero ops not optional, you cannot cut
it out of the software development process. Engineers should do high value work only. -->
