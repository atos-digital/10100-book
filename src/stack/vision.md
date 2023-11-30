# Vision

We use a templating tool [Vision](https://github.com/vision-cli/vision) to produce the scaffolding code that
contains our best practice. It is not necessary to use this tool, Vision is not a dependency, but rather used as
an accelerator.

For example:

Create a project which includes CICD code with:

```bash
vision project create myproject
```

Add a service to your project with:

```bash
cd myproject
vision service create myservice
```

Add the microservice platform code (for Azure in this example):

```bash
vision infra create azure
make infra
```
