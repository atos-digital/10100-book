# Opinionated

In the previous section on [Libraries vs. Frameworkls](./libs.md) we discussed how libraries offer highly skilled
developers the freedom to express their ideas in code, while frameworks programatically constrain developers to
prevent them from making mistakes (which ends up restricting their freedom). Having said that, highly skilled
developers are famously opinionated! They want things done their way and will argue till the ends of the earth
for their opinion (emacs is better than vi!). The difference with frameworks is that opinions can always be
abandoned if there is a good reason, good luck doing that in a framework.

Sometimes opinions have an impact on code quality, and these must be adhered to unless there is a really really good
reason to abandon them. We use
- Coding standards called [The Power of 10100](./power.md)
- Standardised applicatoin scaffolding. We use a tool called [Vision](https://github.com/vision-cli/vision) to reuse our best practice
- Standardised infrastructure. Again we use Vision to generate the infrastructure as code in Terraform or Bicept, creating a standard microservice platform that meets the needs of enterprise. Again no need to debate how to achieve scaling
(Serverless or Kubernetes), no need to debate how to do databases (Managed Postgres), go with the best practice captured in Vision. 

But then sometimes opinions are just a choice and the point is to select one way do it consistently (should 
the open curly appear at the end of the function definition or on the next line?!)
