# jasozh.github.io

A static website written in Svelte that provides details about the LFBI Volunteer Platform.

## CI/CD

The repository is configured with automatic security updates using Dependabot and automatic build testing before each pull request. The CI/CD pipeline consists of the following workflows:

- `deploy.yml` automatically deploys the website to GitHub Pages on every push to the `main` branch.
- `pull-request.yml` runs a sanity check on every opened pull request to make sure the app still builds.
- `dependabot-auto-merge.yml` automatically merges pull requests by Dependabot if it passes the sanity check.

The following GitHub settings are used:

- **Pages > Source: GitHub Actions**
- **Code security > Grouped security updates**
- **General > Allow auto-merge**
- **Branches > Branch protection > Require status checks to pass before merging (pull_request_build)**
