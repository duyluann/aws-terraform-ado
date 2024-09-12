# 🚧 Terraform on Azure Pipeline Project

This repository provides a structured template for Terraform projects, enabling consistent and scalable infrastructure deployments. The template is equipped with best practices, CI/CD integration, and environment-specific configurations to streamline your infrastructure management.

## 📁 Repository Structure

```bash
.
├── .devcontainer
│   ├── Dockerfile                  # 🛠️ Defines the development environment for the project
│   └── devcontainer.json           # 🖥️ Configuration for VSCode Dev Containers
├── .editorconfig                   # 📝 Editor configuration file to maintain consistent coding styles
├── .github
│   ├── ISSUE_TEMPLATE
│   │   └── issue_template.md       # 🗒️ Template for GitHub issues
│   ├── dependabot.yml              # 🤖 Configuration for Dependabot to manage dependencies
│   ├── pull_request_template.md    # 📝 Template for pull requests
│   └── workflows
│       ├── stale.yaml              # 🕰️ Workflow to mark stale issues and PRs
│       └── terraform-aws.yml       # 🚀 CI/CD pipeline for Terraform using GitHub Actions
├── .gitignore                      # 🚫 Specifies files to be ignored by Git
├── .pre-commit-config.yaml         # ✅ Configuration for pre-commit hooks to enforce code quality
├── .terraform.lock.hcl             # 🔒 Lock file to ensure consistent Terraform provider versions
├── .vscode
│   └── extensions.json             # 💻 Recommended VSCode extensions for the project
├── CODEOWNERS                      # 👥 Defines code owners for the repository
├── LICENSE                         # 📜 License for the repository
├── README.md                       # 📖 This file
├── backend.tf                      # 🗄️ Configuration for Terraform backend
├── environments                    # 🌐 Environment-specific variable files
│   ├── dev
│   │   └── dev.tfvars              # 🛠️ Development environment variables
│   ├── prod
│   │   └── prod.tfvars             # 🚀 Production environment variables
│   └── qa
│       └── qa.tfvars               # 🧪 QA environment variables
├── locals.tf                       # 📍 Local values for the Terraform configuration
├── main.tf                         # 🔧 Main Terraform configuration file
├── modules                         # 📦 Directory for reusable Terraform modules
│   └── module1
│       ├── main.tf                 # 🔧 Module-specific configuration
│       ├── outputs.tf              # 📤 Module-specific outputs
│       └── variables.tf            # 📥 Module-specific variables
├── providers.tf                    # 🌐 Provider configurations
└── variables.tf                    # 📥 Input variables for the Terraform configuration
```

## 🚀 Getting Started

### 🧰 Prerequisites

- Terraform: Ensure you have Terraform installed.
- Docker: Required for the development container setup.
- VSCode: Recommended for development, with the Dev Containers extension.

### 🖥️ Development Environment

To get started with development, you can use the pre-configured development container:

1. Open in VSCode:

- Install the Dev Containers extension.
- Open the repository in VSCode.
- You should see a prompt to reopen the project in the dev container.

2. Build and Run:

- The dev container is pre-configured with all the necessary tools and extensions.
- You can start writing and testing your Terraform configurations immediately.

### 🛠️ Terraform Configuration

- Backend Configuration: The `backend.tf` file configures the remote state storage for Terraform.
- Environment Variables: The `environments/` directory contains environment-specific variable files (`.tfvars`).
- Modules: Reusable Terraform modules are stored in the `modules/` directory.

### ✅ Pre-Commit Hooks

Pre-commit hooks are set up to ensure code quality and consistency. To install the pre-commit hooks:

```bash
pre-commit install
```

## ⚙️ Semantic Commit Messages
This project uses [Semantic Commit Messages](https://www.conventionalcommits.org/) to ensure meaningful and consistent commit history. The format is as follows:

```php
<type>(<scope>): <subject>
```

### Types

- `feat`: A new feature (e.g., `feat: add login functionality`).
- `fix`: A bug fix (e.g., `fix: resolve login button issue`).
- `docs`: Documentation changes (e.g., `docs: update API documentation`).
- `style`: Code style changes (formatting, missing semi-colons, etc.) without changing logic (e.g., `style: fix indentation`).
- `refactor`: Code changes that neither fix a bug nor add a feature (e.g., `refactor: update user controller structure`).
- `test`: Adding or updating tests (e.g., `test: add unit tests for login service`).
- `chore`: Changes to build process, auxiliary tools, or libraries (e.g., `chore: update dependencies`).

### Scope

Optional: The part of the codebase affected by the change (e.g., `feat(auth): add OAuth support`)

### Subject

A brief description of the change, using the imperative mood (e.g., `fix: resolve issue with user authentication`).

## 🚀 Semantic Release

This project is configured with [Semantic Release](https://semantic-release.gitbook.io/semantic-release) to automate the release process based on your commit messages.

### How It Works

1. Analyze commits: Semantic Release inspects commit messages to determine the type of changes in the codebase.
2. Generate release version: Based on the commit type, it will automatically bump the version following semantic versioning:
    - fix → Patch release (e.g., 1.0.1)
    - feat → Minor release (e.g., 1.1.0)
    - BREAKING CHANGE → Major release (e.g., 2.0.0)
3. Create release notes: It generates a changelog from the commit messages and includes it in the release.
4. Publish: It automatically publishes the new version to the repository (and any other configured registries, e.g., npm).

## 🤝 Contributing

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Submit a pull request with a detailed description of the changes.

## 📜 License

This project is licensed under the [MIT License](LICENSE).

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
