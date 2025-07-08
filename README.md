# Azure Cloud Resume Challenge

## Overview
This project is my implementation of the [Azure Cloud Resume Challenge](https://cloudresumechallenge.dev/), a hands-on project to build a serverless resume website using Azure services. The website displays my CV with a visitor counter powered by Azure Functions and Cosmos DB.

## Architecture
- **Frontend**: Static website hosted in Azure Blob Storage (`resumestorage123`, `$web` container) utilising HTML and JavaScript (`index.html`, `script.js`).
- **Backend**: Azure Function (`resume-function-123`, Python 3.10, V2 model) that increments a visitor count stored in Cosmos DB (`ResumeDB`, `VisitorCount` container, partition key `/id`).
- **Resource Group**: `cloud-resume`.
- **Technologies**: Azure Blob Storage, Azure Functions, Cosmos DB, JavaScript (fetch API), Azure CLI.

## Steps Completed
1. **HTML Resume**: Created `index.html` with resume content.
2. **Azure Blob Storage**: Set up static website hosting in `resumestorage123`.
3. **Azure Functions**: Built a Python function (`VisitorCounter`) to manage visitor counts.
4. **Cosmos DB**: Configured `ResumeDB` and `VisitorCount` with `/id` partition key.
5. **Function Integration**: Connected the function to Cosmos DB to read/increment/store counts.
6. **Deployment**: Deployed the function using Azure CLI `func azure functionapp publish`.
7. **Frontend Integration**: Updated `script.js` to fetch the count and display it in `index.html`.
8. **Troubleshooting**: Resolved issues like `CosmosResourceNotFoundError`, `Unauthorized`, and `ERR_NAME_NOT_RESOLVED` by fixing Cosmos DB setup, permissions, and CORS.

## Challenges and Solutions
- **Challenge**: `CosmosResourceNotFoundError` in function.
  - **Solution**: Created item (`id="1"`) in `VisitorCount` and added auto-creation logic in `function_app.py`.
- **Challenge**: `ERR_NAME_NOT_RESOLVED` in `script.js`.
  - **Solution**: Corrected Function App URL to `https://resume-function-123.azurewebsites.net/api/VisitorCounter`.
- **Challenge**: "Visitor Count: Error" on website.
  - **Solution**: Configured CORS for `https://resumestorage123.z1.web.core.windows.net`.

## Lessons Learned
- Learned Azure services (Blob Storage, Functions, Cosmos DB) and serverless architecture.
- Mastered troubleshooting CORS, DNS, and Cosmos DB errors.
- Improved Python, JavaScript, and Azure CLI skills.
- Understood secure configuration (e.g., excluding `local.settings.json`).

## Live Demo
- Website: [https://resumestorage123.z1.web.core.windows.net/](https://resumestorage123.z1.web.core.windows.net/)
- API: [resume-function-123.azurewebsites.net/api/VisitorCounter](https://resume-function-123.azurewebsites.net/api/VisitorCounter)

## Next Steps
- Add CSS styling to enhance website appearance.
- Set up CI/CD with GitHub Actions.
- Explore Azure Static Web Apps for integrated hosting.

## Acknowledgments
- Inspired by the [Cloud Resume Challenge](https://cloudresumechallenge.dev/).
- Thanks to Azure docs and community support.