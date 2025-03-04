# Deploying Horusec (SAST) on GitHub and GitLab

## Overview
This repository contains CI/CD configurations to integrate Horusec (a Static Application Security Testing tool) with GitHub Actions and GitLab CI/CD pipelines.

## About Horusec
Horusec is an open-source tool developed by Zup IT for performing static application security testing (SAST). It helps identify security vulnerabilities in source code by analyzing repositories for known issues.

Horusec is similar to SonarQube but is completely free and open source, making it an excellent alternative for teams looking for a cost-effective security scanning solution.
Horusec is an open-source tool developed by Zup IT for performing static application security testing (SAST). It helps identify security vulnerabilities in source code by analyzing repositories for known issues.

### Features of Horusec:
- Supports multiple programming languages.
- Detects security vulnerabilities automatically.
- Can run with or without Docker.
- Generates detailed security reports.

## Requirements
- A GitHub repository with Actions enabled (for GitHub workflow)
- A GitLab repository with a configured runner (for GitLab CI/CD)
- Linux-based environment

## Explanation of Files

### `.github/workflows/.github-workflow.yml`
This file defines a GitHub Actions workflow to automate Horusec security scanning. The workflow:
- Checks out the repository code.
- Installs the Horusec CLI tool.
- Runs Horusec to scan the repository.
- Outputs the results to `horusec_report.txt`.

### `.gitlab-ci.yml`
This file sets up a GitLab CI/CD pipeline to run Horusec scanning. The pipeline:
- Defines a `security` stage.
- Installs the Horusec CLI tool.
- Executes the Horusec scan and saves results to `horusec_report.txt`.
- Cleans the report output by removing unnecessary lines.

## Adding Horusec to Your CI/CD Pipeline
To integrate Horusec into your GitHub Actions or GitLab CI/CD pipeline, ensure that the corresponding configuration files are added to your repository:
- **For GitHub:** Place `.github/workflows/.github-workflow.yml` inside the `.github/workflows/` directory.
- **For GitLab:** Place `.gitlab-ci.yml` in the root directory of your repository.

## Installation & Usage

### GitHub Actions
The `.github/workflows/.github-workflow.yml` file automates Horusec security scanning using GitHub Actions.

#### Steps:
1. **Clone the repository:**
   ```sh
   git clone https://github.com/your-repo.git
   cd your-repo
   ```
2. **Ensure GitHub Actions is enabled** in your repository settings.
3. **Workflow Execution:**
   - The GitHub Action workflow performs the following:
     - Installs Horusec CLI
     - Runs Horusec security scan
   - Results will be available in the `horusec_report.txt` file.

### GitLab CI/CD
The `.gitlab-ci.yml` file sets up a pipeline stage to run Horusec security scanning.

#### Steps:
1. **Ensure a GitLab Runner is set up** and assigned the appropriate tags.
2. **Pipeline Execution:**
   - The GitLab pipeline includes a `security` stage where:
     - Horusec CLI is installed
     - Security scanning is executed
     - The scan results are stored in `horusec_report.txt`
   - The step automatically retries twice in case of failure.

## Notes
- `--disable-docker="true"` is used to ensure the tool runs without Docker.
- The GitLab pipeline removes `Scanning code...` lines from the report for cleaner output.
- Ensure the runner in GitLab has the necessary permissions to execute CI jobs.

