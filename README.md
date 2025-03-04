Deploying Horusec (SAST) on GitHub and GitLab

Overview

This repository contains CI/CD configurations to integrate Horusec (a Static Application Security Testing tool) with GitHub Actions and GitLab CI/CD pipelines.

Requirements

A GitHub repository with Actions enabled (for GitHub workflow)

A GitLab repository with a configured runner (for GitLab CI/CD)

Linux-based environment

Installation & Usage

GitHub Actions

The .github/workflows/.github-workflow.yml file automates Horusec security scanning using GitHub Actions.

Steps:

Clone the repository:

git clone https://github.com/your-repo.git
cd your-repo

Ensure GitHub Actions is enabled in your repository settings.

Workflow Execution:

The GitHub Action workflow performs the following:

Checks out the repository

Installs Horusec CLI

Runs Horusec security scan

Results will be available in the horusec_report.txt file.

GitLab CI/CD

The .gitlab-ci.yml file sets up a pipeline stage to run Horusec security scanning.

Steps:

Ensure a GitLab Runner is set up and assigned the appropriate tags.

Pipeline Execution:

The GitLab pipeline includes a security stage where:

Horusec CLI is installed

Security scanning is executed

The scan results are stored in horusec_report.txt

The step automatically retries twice in case of failure.

Notes

--disable-docker="true" is used to ensure the tool runs without Docker.

The GitLab pipeline removes Scanning code... lines from the report for cleaner output.

Ensure the runner in GitLab has the necessary permissions to execute CI jobs.

Contributions

Feel free to submit issues or pull requests to enhance the security scanning setup!


