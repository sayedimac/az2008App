# az2008App

ASP.NET Core web application with automated deployment to Azure App Service.

## Azure App Service Deployment Setup

This repository includes a GitHub Actions workflow that automatically builds and deploys the application to Azure App Service when changes are pushed to the master branch.

### Prerequisites

1. **Create an Azure Web App**
   - Sign in to the [Azure Portal](https://portal.azure.com)
   - Create a new Web App with .NET 9.0 runtime
   - Note down the app name

2. **Configure GitHub Repository Secrets and Variables**

   **Variables** (Repository Settings > Secrets and variables > Actions > Variables tab):
   - `AZURE_WEBAPP_NAME`: Your Azure Web App name

   **Secrets** (Repository Settings > Secrets and variables > Actions > Secrets tab):
   - `AZURE_WEBAPP_PUBLISH_PROFILE`: 
     1. Go to your Azure Web App in the portal
     2. Click "Get publish profile" 
     3. Download the .PublishSettings file
     4. Copy the entire content of the file
     5. Paste it as the secret value

### Workflow Jobs

- **build**: Restores dependencies, builds, tests, and publishes the application
- **deploy**: Downloads build artifacts and deploys to Azure App Service (only runs on master branch pushes)

### Local Development

```bash
dotnet restore
dotnet build
dotnet run
```

The application will be available at `https://localhost:5001` or `http://localhost:5000`.