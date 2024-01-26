# Bootstrap

The [Vision](https://github.com/vision-cli/vision) tool will create a base 10.10.0 applications scaffolding code.
Vision is not a dependency, but rather used as an accelerator.

For example:

Create a project with:

```bash
vision init myproject
```

Vision will create a myproject folder with a vision.json configuration file.
Change to the myproject folder and initialise the 10100 plugin with the module name of your project in the form github.com/org/domain/subdomain...

```bash
cd myproject
vision 10100 init github.com/myorg/myapp
```

Generate the scaffolding code

```bash
vision 10100 generate
```

Vision will create a folder called myapp with the base 10.10.0 app. You can run the app with

```bash
cd myapp
make
```

You will be able to access the app at http://localhost:8080
