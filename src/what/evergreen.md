# 10+ years evergreen

## The status quo

We see three frequent issues in enterprise IT systems today that reduce the lifespan of their software, requiring teams to spend time and resources engaging in endless upgrade cycles.

### Legacy frameworks

The IT systems of many older organisations are built using legacy frameworks which lack the capabilities and efficiency of newer solutions, and which can hamper performance, security, and integration with modern technologies. This restricts the organisation’s ability to adopt new tools and standards, and to extend existing systems as new requirements and standards are introduced.

Closed ecosystems from vendors can also limit the ability to integrate with new technologies and services, creating a vendor lock-in which can be costly both to maintain and to migrate away from.

### Volatile technologies

Many IT systems are also built on highly volatile technologies which change rapidly with every upgrade cycle, requiring teams to continuously learn and adapt to new standards and syntax. These technologies also tend to have a short lifespan and are usually only supported for between 1.5 and 3 years, often requiring code rewrites when versions reach end of life. This forces organisations to dedicate significant resources to keep up with the pace of upgrades or risk falling out of date, exposing them to security vulnerabilities and creating a fragmented IT system with components running on different versions.

### Reliance on direct and indirect dependencies

Many applications these days are built on tens, if not hundreds of dependencies, whether direct or indirect. The average Javascript dependency, for instance, has 79 other transitive dependencies, all of which have their own release cycle and compatibility considerations. This can force teams into “dependency hell”, where developers spend more time managing and resolving dependency-related issues like conflicting versions and incompatible libraries than working on new features or improvements.

All these dependencies are also potential vectors of attack – [Sonatype’s 2023 report on the software supply chain industry](https://www.sonatype.com/state-of-the-software-supply-chain/open-source-supply-and-demand) noted that it had detected 245,032 malicious packages detected across the various open-source ecosystems in 2023, triple the number in 2022.

## Our approach

We advocate building software using a small, core set of current technologies which prioritise stability and backwards-compatibility. The primary backend language that we use is [Go](https://go.dev/), which has been backwards-compatible and syntactically consistent since its public release in 2009. In all that time, Go has remained on version 1, and the [co-founder of Go recently reaffirmed the language’s commitment to compatibility](https://go.dev/blog/compat), emphasising that “Go 2, in the sense of breaking with the past and no longer compiling old programs, is never going to happen”. With Go, entire apps can be automatically migrated to the latest version and benefit from the latest security patches and QoL upgrades, with no need for rewrites or upgrades.

We also support avoiding reliance on bloated frameworks or tools which introduce a large number of third-party dependencies. Any dependencies which we do use, such as [htmx](https://htmx.org/) for frontend interactivity, are deliberately selected because they are lightweight, have a stable track record, and have no transitive dependencies.

Using this approach, we envision that software will remain “evergreen” for at least 10 years, which means that it will stay up to date through a continuous, incremental, and automatic upgrading process. This allows users to benefit from a smoother upgrade process, new features, and security patches, while requiring little manual intervention from the provider and freeing teams up to develop new features and products.

<!-- Yes we know its an oxymoron but its catchy with the right
technology stack and design choices, we can build software that performs its function and
stays up to date without the need for (much) intervention after it has been built. This is a particularly attractive idea in enterprise because they often "finish" an application and
then do not want to keep teams feeding and watering those application until a new feature comes along.Today we see teams having to spend months upgrading software before adding new features to
an application that is mission critical but has had no need for development in years. -->
