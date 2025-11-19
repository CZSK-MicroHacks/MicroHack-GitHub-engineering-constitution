# Bicep Engineering Standard

## 1. Scope
Applies to all Infrastructure as Code (IaC) projects using Bicep within MicroHack teams.

## 2. Tooling
- **Bicep CLI**: Use the latest stable version of the Bicep CLI.
- **VS Code Extension**: Use the official Bicep extension for syntax highlighting, validation, and intellisense.

## 3. Project Structure
- **Modules**: Break down complex deployments into smaller, reusable modules.
- **Main Entry Point**: Use a `main.bicep` file to orchestrate the deployment of modules.
- **Parameter Files**: Use `.bicepparam` files or JSON parameter files to manage environment-specific values.

## 4. Coding Conventions
### Parameters
- **Naming**: Use clear, descriptive names (camelCase). Consistent naming makes templates easier to read.
- **Usage**: Use parameters for settings that change between deployments (e.g., environment names, SKUs).
- **Defaults**: Provide safe default values (e.g., low-cost SKUs for dev).
- **Descriptions**: Always provide `@description()` decorators for parameters to explain their purpose and constraints.
- **Constraints**: Use `@allowed()`, `@minLength()`, `@maxLength()` decorators to prevent invalid inputs, but use `@allowed()` sparingly to avoid blocking valid future SKUs.
- **Location**: Place parameter declarations at the top of the file.

### Variables
- **Usage**: Use variables for logic and values that do not change between deployments or are derived from parameters.
- **Type Inference**: Do not specify types for variables; let Bicep infer them.
- **No Suffixes**: Avoid distinguishing variables and parameters by suffixes (e.g., `storageAccountNameParam`).

### Names
- **Casing**: Use `lowerCamelCase` for symbolic names (e.g., `myResource`).
- **Uniqueness**: Use `uniqueString()` with `resourceGroup().id` for globally unique names, but combine it with meaningful prefixes (e.g., `${appName}-${env}-${uniqueString(...)}`).
- **Symbolic Names**: Avoid using `name` in the symbolic name (e.g., use `cosmosAccount` instead of `cosmosAccountName`).

### Resource Definitions
- **Symbolic References**: Use symbolic names to reference other resources (e.g., `storageAccount.id`) instead of `resourceId()` or `reference()`. This creates implicit dependencies.
- **Implicit Dependencies**: Prefer implicit dependencies (referencing properties) over explicit `dependsOn`.
- **Existing Resources**: Use the `existing` keyword to reference resources not deployed in the current file.
- **API Versions**: Use recent API versions to access the latest features.

### Child Resources
- **Nesting**: Avoid deep nesting. Use the `parent` property for child resources to keep code flat and readable.
- **Naming**: Do not construct names for child resources manually; let Bicep handle the hierarchy.

### Outputs
- **Sensitive Data**: Use `@secure()` decorator for sensitive outputs to prevent logging.
- **Resource Lookup**: Instead of passing resource IDs as outputs, prefer looking up resources in the consuming template using `existing` keyword where possible.

## 5. Security
- **Secrets**: Use Key Vault references in parameter files for secrets. Never hardcode secrets.
- **Secure Parameters**: Mark password or secret parameters with `@secure()`.

## 6. CI/CD Expectations
- **Validation**: Run `az bicep build` to validate syntax and `az deployment group validate` to check deployment logic.
- **What-If**: Use `az deployment group what-if` in PR pipelines to preview changes.
- **Linting**: Fix all warnings reported by the Bicep linter.
