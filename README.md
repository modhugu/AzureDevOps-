AzureDevOpsTemplates

Small, reusable Azure DevOps pipeline templates for building .NET Core and Maven projects. Drop these templates into any repo (or reference them centrally) to standardize build, test, publish and artifact steps.

What's included
- `dotnetcore/dotnetcore-build.yaml` — build, (optional) test, publish and artifact publish for .NET Core projects.
- `maven/maven-build.yaml` — parameterized Maven build that publishes JUnit results and artifacts.
- `maven/maven-build-jfrog.yaml` — Maven build using JFrog tasks for resolve/deploy and publishing build info.
- `maven/maven-pipeline.yaml` — small example showing variable group usage and template call.

Quick use (examples)
- .NET Core (in your `azure-pipelines.yml`):

```yaml
- template: dotnetcore/dotnetcore-build.yaml
	parameters:
		mainproject: '**/*.csproj'
		runTests: true
```

- Maven:

```yaml
- template: maven/maven-build.yaml
	parameters:
		goal: 'package'
		artifactsPath: '**/*.jar'
```

Notes
- Templates are parameterized; check the top of each YAML for available parameters and defaults.
- For JFrog templates you must create an Artifactory service connection in the Azure DevOps project and pass its name via `artifactoryConnection`.
- Secure secrets using variable groups and service connections; do not hardcode credentials.



