# testGradle

Simple repo to demonstrate a bug.

## usage

```bash
gradle build
ll **/build/distributions/
sam build
du -sh .aws-sam/build/*
```

## Example output

```bash
$ gradle build

BUILD SUCCESSFUL in 3s
7 actionable tasks: 7 executed

$ ll **/build/distributions/
HelloWorldFunction/build/distributions/:
total 8
-rw-r--r--  1 ajshearn  staff   2.4K  2 Mar 14:25 HelloWorldFunction.zip

layers/build/distributions/:
total 1712
-rw-r--r--  1 ajshearn  staff   853K  2 Mar 14:25 layers.zip

$ sam build
Your template contains a resource with logical ID "ServerlessRestApi", which is a reserved logical ID in AWS SAM. It could result in unexpected behaviors and is not recommended.
Test the latest build changes for Java runtime 'SAM_CLI_BETA_MAVEN_SCOPE_AND_LAYER=1 sam build'. These changes will replace the existing flow on 1st of April 2022. Check https://github.com/aws/aws-sam-cli/issues/3639 for more information.
Building layer 'libs'
Running JavaGradleWorkflow:GradleBuild
Running JavaGradleWorkflow:JavaGradleCopyArtifacts
Building codeuri: /Users/ajshearn/repos/opensource/testGradle/HelloWorldFunction runtime: java11 metadata: {} architecture: arm64 functions: ['HelloWorldFunction']
Running JavaGradleWorkflow:GradleBuild
Running JavaGradleWorkflow:JavaGradleCopyArtifacts

Build Succeeded

Built Artifacts  : .aws-sam/build
Built Template   : .aws-sam/build/template.yaml

Commands you can use next
=========================
[*] Invoke Function: sam local invoke
[*] Test Function in the Cloud: sam sync --stack-name {stack-name} --watch
[*] Deploy: sam deploy --guided

$ du -sh .aws-sam/build/*
1.0M	.aws-sam/build/HelloWorldFunction
1.0M	.aws-sam/build/libs
4.0K	.aws-sam/build/template.yaml
```

Note the `HelloWorldFunction` and `libs` folders have the same size. They should
not.
