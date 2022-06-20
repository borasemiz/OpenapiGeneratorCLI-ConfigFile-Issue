# Readme

First, you need to install the node dependencies with the following command in the project's root directory:

```
$ npm install
```

The `master` branch contains the state which doesn't work. The spec and generator config file is located inside `tools-config` directory. In the root of this project, in command line, execute:

```
$ ./node_modules/.bin/openapi-generator-cli generate --config tools-config/openapitools.json
```

This command fails to read the contents of `tools-config/openapitools.json` and throws this error in the terminal:

```
Exception in thread "main" java.lang.NullPointerException: generator name must be specified
        at java.util.Objects.requireNonNull(Unknown Source)
        at org.apache.commons.lang3.Validate.notEmpty(Validate.java:388)
        at org.openapitools.codegen.config.CodegenConfigurator.toContext(CodegenConfigurator.java:498)
        at org.openapitools.codegen.config.CodegenConfigurator.toClientOptInput(CodegenConfigurator.java:599)
        at org.openapitools.codegen.cmd.Generate.execute(Generate.java:441)
        at org.openapitools.codegen.cmd.OpenApiGeneratorCommand.run(OpenApiGeneratorCommand.java:32)
        at org.openapitools.codegen.OpenAPIGenerator.main(OpenAPIGenerator.java:66)
```

In addition to that, it creates a new `openapitools.json` in the root of the project, which doesn't contain any generator config.

What this command should do is that it should read the contents of `tools-config/openapitools.json` and generates the API client according to the configuration described in that file. It shouldn't fail with error.

`openapitools.json` is only read IF it is in the same directory where the `openapi-generator-cli generate` command is executed. If you switch to the `working` branch, you will see it. Switch to the `working` branch and do:

```
$ ./node_modules/.bin/openapi-generator-cli generate
```

It will successfuly generate the API client in `generated` folder.
