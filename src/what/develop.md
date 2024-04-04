# 10 weeks to develop

## Existing approaches

Enterprises tend to have longer development cycles for features than necessary mainly due to two factors.

### Complex decision-making processes

Large enterprises often have complex requirements which involve multiple departments, each with its own set of processes and priorities. Coordinating efforts across these diverse units can drive complexity in the software development workflow which has the effect of adding layers of project management, business analysis, etc and driving developers further and further apart from users. This creates large amounts of Work In Progress (WIP), long feedback cycles, and increases development time, increasing costs and the risk that the project doesn't deliver what users need.

### Older, heterogenous tech stacks

Many enterprises rely on legacy systems that are deeply ingrained in their operations, which may lack the flexibility and efficiency of newer tools, receive limited support, and have accumulated technical debt over time. To compound the problem, large enterprises have typically acquired many smaller organisations over their lifetimes, leaving them with a heterogeneous ecosystem comprised of numerous different technologies. The use of such older and disparate technologies can hinder compatibility with modern tooling and reduce flexibility, requiring custom solutions and increasing time to deployment.

## The 10.10.0 approach

10.10.0 adopts a simplified development workflow and a standardised, opinionated modern tech stack.

### Simplified development workflow

Use the most lean development system appropriate to your circumstance, preferably something light-weight like [Kanban](<https://en.wikipedia.org/wiki/Kanban_(development)>). **Developers work directly with users** in actively guiding the trajectory of the product, identifying features, breaking down work into small chunks (no more than a week) and prioritising the development effort. This leads to smaller WIP, much shorter feedback cycles, and the product tracking much closer to user needs, reducing the risk of cost overruns and missing business goals.

### Standardised, opinionated tech stack

Use the 10.10.0 tech stack based on a [Golang](https://go.dev) and [HTMX](https://htmx.org). This tech stack avoids the constant upgrade cycles of frameworks such as [dotnet](https://dotnet.microsoft.com/en-us/) or [spring](https://spring.io), and sprawling dependencies with their complex supply chains.

Use the opinionated 10.10.0 application [template](https://github.com/atos-digital/10.10.0-template) that comes with a standardised design patterns, CI/CD pipeline, linters, and mature libraries to reduce the time and effort spent on getting started and enforcing good practices.

Optionally the tool [vision](https://github.com/vision-cli/vision) can be used to bootstrap a project with this template.
