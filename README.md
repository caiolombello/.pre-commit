# Project Setup with Pre-Commit

This repository is configured with **pre-commit** to ensure code quality through automatic checks before each commit. **Pre-commit** runs hooks such as linting, formatting, and security checks to ensure that the code follows best practices.

## Requirements

Before setting up the project, ensure you have the following installed:

- **Python** (>= 3.6) and **pip**
- **Git**

## Setup Steps

### 1. Install `pre-commit`

**Pre-commit** is a tool that manages and installs Git hooks that run before committing your code.

#### Using `pip`:

Run the following command to install **pre-commit**:

```bash
pip install pre-commit
```

### 2. Install Pre-Commit Hooks

Once **pre-commit** is installed, you need to configure Git to use the hooks defined in this repository. To do this, run:

```bash
pre-commit install
```

This will install the hooks into the `.git/hooks/` directory, and **pre-commit** will automatically run before every commit.

### 3. Run Hooks on All Files

When adding new hooks, it’s a good idea to run them on all files to ensure the existing code adheres to the checks. You can do this with:

```bash
pre-commit run --all-files
```

### 4. Update Hooks (Optional)

To ensure you are always using the latest versions of the hooks, you can run:

```bash
pre-commit autoupdate
```

This will update all hooks to their latest compatible versions.

## Configured Hooks

The following hooks are configured in this repository:

- **GitLeaks**: Detects hardcoded secrets in the code.
- **Pre-Commit Hooks**:
  - `trailing-whitespace`: Removes trailing whitespace from lines.
  - `end-of-file-fixer`: Ensures that files end with a newline.
  - `check-yaml`: Checks that YAML files are correctly formatted.
  - `check-merge-conflict`: Detects unresolved merge conflicts.
  - `detect-private-key`: Detects private keys that may have been added to the repository.
- **Ruff**: Linter and code formatter for Python.
- **ESLint**: Linter for JavaScript files.
- **Hadolint**: Linter for Dockerfiles to ensure best practices.
- **Terraform**:
  - `terraform_fmt`: Formats Terraform configuration files.
  - `terraform_validate`: Validates Terraform configuration and syntax.
- **TFLint**: Additional linting for Terraform to catch common issues.

## Temporarily Disabling Hooks

If you need to make a commit without running a specific hook, you can use the following command:

```bash
SKIP=<hook-id> git commit -m "Your commit message"
```

For example, to skip the `end-of-file-fixer`:

```bash
SKIP=end-of-file-fixer git commit -m "Commit message"
```

## Maintenance

To keep the pre-commit hooks updated, run:

```bash
pre-commit autoupdate
```

This will ensure that you are using the latest versions of all configured hooks.
