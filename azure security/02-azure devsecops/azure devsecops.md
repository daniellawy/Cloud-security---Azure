# DevSecOps

## Objective

Secure an Azure-hosted application through Azure DevOps by reviewing the repository, securing the deployment pipeline, and enforcing branch protection.

## 1. Access Azure DevOps

Sign in to https://dev.azure.com using credentials. Open the assigned Azure DevOps project.

The project provides access to the main DevOps services:

```text id="8r4nq1"
Azure DevOps Project
├── Boards
├── Repos
├── Pipelines
├── Test Plans
└── Artifacts
```

![Azure DevOps project](screenshots/01-azure-devops-project.png)

## 2. Navigate to Azure Repos

Open:

**Repos → Files**

Locate the application source repository and review the repository structure.

The deployment pipeline was located at:

```text id="x2q8fz"
deploy-web-app.yml
```

![Azure Repos](screenshots/02-azure-repos.png)

## 3. Review the Deployment Pipeline

Open `deploy-web-app.yml` and review the existing deployment tasks.

The pipeline uses `AzureCLI@2` to execute Azure CLI commands during deployment.

The existing App Service deployment task checks whether the application exists before creating the required resources.

```yaml id="4h7m2p"
- task: AzureCLI@2
  displayName: 'Create App Service if not exists'
  inputs:
    azureSubscription: $(azureSubscription)
    scriptType: 'bash'
    scriptLocation: 'inlineScript'
    inlineScript: |
      if ! az webapp show --name $(appName) --resource-group $(resourceGroup) &> /dev/null; then
        echo "App Service does not exist. Creating..."
        az appservice plan create --name $(appName)-plan --resource-group $(resourceGroup) --location $(location) --sku $(sku) --is-linux
        az webapp create --name $(appName) --resource-group $(resourceGroup) --plan $(appName)-plan --runtime "$(runtimeStack)"
      else
        echo "App Service $(appName) already exists."
      fi
```

![Deployment YAML](screenshots/03-deployment-yaml.png)

## 4. Add App Service Security Controls

Add a new `AzureCLI@2` task below the existing App Service configuration tasks.

The task configures HTTPS-only access and requires TLS 1.2:

```yaml id="c6t9vk"
- task: AzureCLI@2
  displayName: 'Apply Security Controls to App Service'
  inputs:
    azureSubscription: $(azureSubscription)
    scriptType: 'bash'
    scriptLocation: 'inlineScript'
    inlineScript: |
      az webapp config set --name $(appName) --resource-group $(resourceGroup) --httpsOnly=true --min-tls-version 1.2
```

The security configuration is therefore applied automatically whenever the deployment pipeline runs.

![Security controls in pipeline](screenshots/04-pipeline-security-controls.png)

## 5. Commit the Pipeline Changes

After editing `deploy-web-app.yml`:

1. Select **Commit**.
2. Review the changes.
3. Confirm the commit.

The pipeline security configuration is now stored in source control.

![Pipeline commit](screenshots/05-pipeline-commit.png)

## 6. Configure Branch Policies

Navigate to:

**Repos → Branches**

Find the `main` branch and open:

**⋯ → Branch policies**

Enable:

**Require a minimum number of reviewers**

Configure the policy to require **2 reviewers**.

Keep:

**Allow requestors to approve their own changes**

disabled.

![Branch policies](screenshots/06-branch-policies.png)

## 7. Save the Branch Policy

Select **Save**.

The `main` branch now requires the configured reviewers before changes can be merged.

![Saved branch policy](screenshots/07-branch-policy-saved.png)

## CI/CD Security Flow

```text id="j5v1ke"
Code change
    ↓
Azure Repos
    ↓
main branch policy
    ↓
Required code review
    ↓
Azure Pipeline
    ↓
Azure CLI deployment
    ↓
App Service
    ↓
HTTPS + TLS 1.2
```

## Result

The Azure DevOps project was reviewed across **Repos** and **Pipelines**.

The deployment pipeline was modified to enforce **HTTPS** and **TLS 1.2** on the App Service, and the `main` branch was protected by requiring two reviewers with self-approval disabled.

These controls add security checks at both the **source-control** and **deployment** stages of the CI/CD workflow.
