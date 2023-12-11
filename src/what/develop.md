# 10 weeks to develop

## The status quo

Traditional enterprises tend to require more time to adopt and integrate new technologies in comparison to their digital native counterparts, which are able to develop, test, and deploy new features and products in a matter of months or even weeks. We think that this protracted development timeline is due mainly to two factors.

### Complex decision-making processes

Large enterprises often have complex requirements which involve multiple departments, each with its own set of processes and priorities. Coordinating efforts across these diverse units can be challenging, increasing time for decision-making and implementation processes. Additionally, developers tend to have little direct communication with the client and must interface through project managers, creating a long feedback cycle and increasing development time.

### Older, heterogenous tech stacks

Many enterprises rely on legacy systems that are deeply ingrained in their operations, which may lack the flexibility and efficiency of newer tools, receive limited support, and have accumulated technical debt over time. To compound the problem, large enterprises have typically acquired many smaller organisations over their lifetimes, leaving them with a heterogeneous tech stack comprised of numerous different technologies. The use of such older and disparate technologies can hinder compatibility with modern tooling and reduce flexibility, requiring custom solutions and increasing time to deployment.

## Our approach

To make enterprises more agile, we advocate adopting a simplified development workflow and a standardised, opinionated modern tech stack.

### Simplified development workflow

We believe developers should be empowered to work directly with the users of their product and take an active role in guiding the trajectory of the project. This leads to faster communication and a much shorter feedback cycle, allowing for rapid iteration – dev teams should be discussing product requirements with the client instead of receiving them passively through an intermediary, building prototypes in a matter of days, and getting direct feedback from the client for the next round of iteration. Teams should adhere to certain industry best practices such as the [Twelve-Factor App methodology](https://12factor.net/) to standardise the development workflow, and complex project management processes which may hinder the speed of development should be carefully reviewed and followed only if necessary.

### Standardised, opinionated tech stack

Enterprises should adopt a standardised, opinionated tech stack comprised of modern tools and languages, avoiding ecosystems which involve heavy tooling, ever-changing frameworks, and large software supply chains where possible. Golang and HTMX are strong examples of such highly productive modern technologies.

Additionally, standardised formatting, linters, design patterns and mature standard libraries should be integrated into the build process and enforced by an automated CI/CD pipeline, reducing the time and effort spent on enforcing good practices and enabling a shift to rapid small deployments. This is an approach already adopted by agile digital native companies - for example, [Github deploys to production as often as 20 times a day](https://github.blog/2023-04-06-building-github-with-ruby-and-rails/). This eliminates the need for developers to worry about planning and coordinating “big bang releases”, freeing them up to focus on code.

By utilising a modern stack built with automation in mind and with predefined standards, teams can dramatically reduce the time it takes to go from zero to production, from years to a matter of months.

<!-- Freeing up developers to work at the speed they want to go. Interacting directly with business users. Building prototypes in days and deploying working software in weeks. Iterating at the speed of light, using the software to drive business
change instead of the all too familiar problem of software holding business back.
This is not a new idea and we see many enterprises succeeding. But unfortunately many
fail, spending a lot of money on the wrong things (like the very expensive ecosystem
of application suppliers that have built up around enterprise, a particular bugbear of ours). -->
