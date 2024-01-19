# 10+ years evergreen

Two key issues reduce the lifespan of enterprise software.

### Volatile technologies

Many applications are built on technologies that change every few years and then trigger an upgrade cycle in their dependent apps. Two very common examples are [dotnet](https://dotnet.microsoft.com/en-us/) and [java](https://www.java.com/en/), and to some extent even the python ecosystem. Teams must to continuously learn and adapt to new standards and syntax and apps sometimes require rewrites such as dotnet framework to dotnet core, python 2 to 3, etc. This forces enterprises to dedicate significant resources to keep up with the pace of upgrades or risk falling out of date, exposing them to security vulnerabilities and creating a fragmented IT system with components running on different versions.

### Reliance on direct and indirect dependencies

Many applications these days are built on tens, if not hundreds of dependencies, whether direct or indirect. The average Javascript dependency, for instance, has 79 other transitive dependencies, all of which have their own release cycle and compatibility considerations. This can force teams into “dependency hell”, where developers spend more time managing and resolving dependency-related issues like conflicting versions and incompatible libraries than working on new features or improvements.

All these dependencies are also potential vectors of attack – [Sonatype’s 2023 report on the software supply chain industry](https://www.sonatype.com/state-of-the-software-supply-chain/open-source-supply-and-demand) noted that it had detected 245,032 malicious packages detected across the various open-source ecosystems in 2023, triple the number in 2022.

## Our approach

We advocate building software using a small, core set of current technologies which prioritise stability and backwards-compatibility. The primary backend language that we use is [Go](https://go.dev/), which has been backwards-compatible and syntactically consistent since its public release in 2009. In all that time, Go has remained on version 1, and the [co-founder of Go recently reaffirmed the language’s commitment to compatibility](https://go.dev/blog/compat), emphasising that “Go 2, in the sense of breaking with the past and no longer compiling old programs, is never going to happen”. With Go, entire apps can be automatically migrated to the latest version and benefit from the latest security patches and QoL upgrades, with no need for rewrites or upgrades.

We also support avoiding reliance on bloated frameworks or tools which introduce a large number of third-party dependencies. Any dependencies which we do use, such as [htmx](https://htmx.org/) for frontend interactivity, are deliberately selected because they are lightweight, have a stable track record, and have no transitive dependencies.

Using this approach, we envision that software will remain “evergreen”, which means enterprise software development teams can write an app and "fire and forget" without having to worry about constant upgrades or supply chain issues.
