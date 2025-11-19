# Terraform Engineering Standard

## 1. Scope
Applies to all Infrastructure as Code (IaC) projects using Terraform within MicroHack teams.

## 2. Tooling & Providers
- **Terraform Version**: Use the latest stable version of Terraform. Pin versions in `terraform` block to avoid accidental upgrades.
- **Providers**:
  - Use `azurerm` for standard Azure resources.
  - Use `azapi` for bleeding-edge features unsupported in `azurerm`.
  - Pin provider versions to ensure reproducible builds.

## 3. Project Structure
- **File Organization**:
  - Segment resource types into separate files: `networking.tf`, `service_bus.tf`, `rbac.tf`, etc.
  - If a type bloats, split further by function: `container_app.frontend.tf`, `container_app.backend.tf`.
  - Keep `main.tf` for provider configuration and backend setup.
  - Use `variables.tf` for input variables and `outputs.tf` for output values.
  - Use `versions.tf` for provider and terraform version constraints.

## 4. Coding Conventions
- **Variables**:
  - Always include rich multi-line descriptions: purpose, type, constraints, examples.
  - Provide sensible defaults where safe.
  - Use specific types (e.g., `list(string)`, `object({...})`) instead of `any`.
- **Comments**:
  - Only for non-obvious attributes or critical justification.
  - No change logs, no progress notes.
- **Tags**:
  - Tags are optional unless explicitly requested.
  - If used, prefer a `locals` block to define common tags applied to all resources.
- **Naming**:
  - Use `snake_case` for resource names and variables.
  - Resource names should be descriptive and unique within the module.

## 5. State Management
- **Remote State**: Always use a remote backend (e.g., Azure Storage Account) for state files. Never commit `terraform.tfstate` to version control.
- **State Locking**: Ensure the backend supports state locking (Azure Storage supports this via leases) to prevent concurrent modifications.
- **State Isolation**: Use separate state files for different environments (dev, staging, prod) to limit blast radius.

## 6. Modules
- **Modularity**: Encapsulate reusable logic in modules.
- **Versioning**: Version modules using semantic versioning tags in git.
- **Sources**: Prefer local paths for monorepo modules or git URLs with tags for shared modules.

## 7. Security
- **Secrets**: Never hardcode secrets in `.tf` files. Use Azure Key Vault or environment variables.
- **Sensitive Data**: Mark sensitive output values with `sensitive = true` to prevent them from being shown in CLI output.

## 8. CI/CD Expectations
- **Workflow**:
  - **PR**: Run `terraform fmt -check`, `terraform validate`, and `terraform plan`.
  - **Merge**: Run `terraform apply` (auto-approve) on the main branch or via manual approval gate.
- **Formatting**: Enforce `terraform fmt` in CI.
- **Linting**: Use `tflint` to catch common errors and enforce best practices.
