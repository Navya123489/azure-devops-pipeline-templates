# azure-devops-pipeline-templates
Reusable Azure DevOps YAML pipeline templates for build, test, and deploy workflows

# Azure DevOps Pipeline Templates

Reusable Azure DevOps YAML pipeline templates for build, 
test, security scanning, and deployment workflows.

## Structure
templates/          # Reusable pipeline templates
├── build-template.yml          # Build, test and publish
├── deploy-template.yml         # Environment deployment
└── security-scan-template.yml  # Dependency and secret scanning
examples/           # Complete pipeline examples
├── dotnet-app-pipeline.yml     # End-to-end .NET app pipeline
└── docker-pipeline.yml         # Docker build and push to ACR

## Templates

### build-template.yml
Reusable build stage for .NET applications. Handles:
- .NET SDK installation
- NuGet package restore
- Build and compile
- Unit test execution with code coverage
- Artifact publishing

### deploy-template.yml
Reusable deployment stage with environment approvals. Handles:
- Artifact download
- Azure Web App deployment
- Post-deployment smoke testing
- Build tagging

### security-scan-template.yml
Reusable security scanning stage. Handles:
- Dependency vulnerability scanning
- Hardcoded secret detection
- Configurable fail-on-severity behaviour

## How to use

Reference these templates in your own pipeline:

```yaml
stages:
  - template: templates/build-template.yml
    parameters:
      buildConfiguration: 'Release'
      dotnetVersion: '8.0.x'
      runTests: true

  - template: templates/deploy-template.yml
    parameters:
      environment: 'dev'
      azureSubscription: 'MySubscription'
      webAppName: 'my-web-app'
```

## Requirements
- Azure DevOps organisation
- Azure subscription connected as a service connection
- Self-hosted or Microsoft-hosted agents

## Author
Navya Kanchisamudram — Azure Administrator (AZ-104) 
| AZ-400 DevOps Engineer — In Progress
