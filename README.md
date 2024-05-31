
### CI/CD README

Create a new file at `./docs/cicd-readme.md`:

```markdown
# CI/CD Pipeline

## Overview

This repository uses GitHub Actions for Continuous Integration and Continuous Deployment (CI/CD). The pipeline is designed to build, test, and deploy the application to AWS across three environments: Development (Dev), Testing (Test), and Staging (STG).

## Environments

- **Dev**: Deploys on every push to the `develop` branch.
- **Test**: Deploys if the deployment to Dev is successful.
- **STG**: Deploys only when the target branch of the merge request is the `master` branch.

## Workflow File

The CI/CD pipeline is defined in the GitHub Actions workflow file located at `.github/workflows/pipeline.yml`.

## Workflow Steps

1. **Build**:
   - Triggered on push to `develop` and `master` branches.
   - Checks out the code.
   - Sets up Node.js.
   - Installs dependencies.
   - Runs tests.

2. **Deploy to Dev**:
   - Triggered if the build step is successful and the branch is `develop`.
   - Deploys the application to the Dev environment.

3. **Deploy to Test**:
   - Triggered if the Dev deployment is successful and the branch is `develop`.
   - Deploys the application to the Test environment.

4. **Deploy to STG**:
   - Triggered on push to the `master` branch.
   - Deploys the application to the STG environment.

## AWS Configuration

The deployment steps use the AWS CLI to sync the build artifacts to the respective S3 buckets or other AWS services. Ensure the following AWS credentials are added to your repository secrets:

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_REGION`

## Branch Protection Rules

To ensure the integrity of the `master` branch, it is protected with the following rules:

- Only repository owners can merge into `master`.
- Pull requests require approval before merging.
- Status checks must pass before merging.

## How to Trigger the Pipeline

- **For Dev and Test Environments**: Push your changes to the `develop` branch. If the Dev deployment succeeds, the pipeline will automatically proceed to deploy to the Test environment.
- **For STG Environment**: Merge changes into the `master` branch through a pull request. Ensure all required reviews and status checks are completed.

## Troubleshooting

- Check the Actions tab in GitHub for detailed logs of each step.
- Ensure your AWS credentials and environment variables are correctly configured.
- Verify that your branch protection rules are correctly set up in the repository settings.

## Contributing to CI/CD

1. Update the workflow file `.github/workflows/pipeline.yml` as needed.
2. Ensure your changes are tested by pushing to a feature branch and observing the pipeline behavior.
3. Submit a pull request with your updates.

## License

This project is licensed under the MIT License - see the [LICENSE](../LICENSE) file for details.
