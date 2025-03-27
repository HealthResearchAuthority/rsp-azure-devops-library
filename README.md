# Azure DevOps Library for IRAS

This repository contains reusable YAML templates and scripts for Azure DevOps pipelines. It is designed to streamline CI/CD processes, automate testing, and ensure code quality for projects within the IRAS ecosystem.

## Repository Structure

```
LICENSE
README.md
docs/
jobs/
steps/
```

### Key Directories

- **`docs/`**: Documentation files, including templates for pull requests.
- **`jobs/`**: YAML files defining reusable pipeline jobs, such as `build`, `deploy`, and `test`.
- **`steps/`**: Modular YAML templates for individual pipeline steps, organized by functionality (e.g., `automationtests`, `codeanalysis`, `dotnet`, etc.).

## Getting Started

### Prerequisites

- Azure DevOps account
- Access to the repository
- Required Azure DevOps service connections (e.g., `service_connection`, `ACR Dev Connection`)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-org/rsp-azure-devops-library.git
   cd rsp-azure-devops-library
   ```

2. Integrate the YAML templates into your Azure DevOps pipelines by referencing them in your pipeline definitions.

### Usage

- Reference jobs in your pipeline YAML files:
  ```yaml
  jobs:
    - template: jobs/build.yaml
      parameters:
        run_github_security_scan: true
        sonar_project_key: 'your-project-key'
        sonar_project_name: 'your-project-name'
  ```

- Reference steps in your pipeline YAML files:
  ```yaml
  steps:
    - template: steps/dotnet/build.yaml
      parameters:
        checkout: true
  ```

## Features

- **Build Automation**: Templates for building .NET projects, restoring dependencies, and generating reports.
- **Testing**: Support for unit tests, API tests, and end-to-end tests using tools like Playwright and Newman.
- **Code Quality**: Integration with SonarCloud for static code analysis and quality gate validation.
- **Security**: Dependency scanning and CodeQL analysis for identifying vulnerabilities.
- **Deployment**: Templates for deploying to Azure App Services, Azure Functions, and Azure Container Apps.
- **Reporting**: Automated publishing of test reports and code coverage results.

## Build and Test

### Build

Use the `build.yaml` job to automate the build process:
```yaml
jobs:
  - template: build.yaml
    parameters:
      run_github_security_scan: true
      run_sonarcloud_analysis: true
```

### Test

Run unit tests, API tests, or end-to-end tests using the respective templates:
```yaml
jobs:
  - template: api_tests.yaml
    parameters:
      reportDirectory: 'test-reports'
      upload_to_sharepoint: false
```

## Contributing

We welcome contributions to improve this library. To contribute:

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes with clear commit messages.
4. Submit a pull request.

Please ensure your code adheres to the repository's coding standards and passes all tests.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Support

For questions or support, please contact the repository maintainers or open an issue in the repository.