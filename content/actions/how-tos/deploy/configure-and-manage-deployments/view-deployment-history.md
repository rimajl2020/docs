---
title: Viewing deployment history
shortTitle: View deployment history
intro: View current and previous deployments for your repository.
versions:
  fpt: '*'
  ghes: '*'
  ghec: '*'
topics:
  - API
redirect_from:
  - /developers/overview/viewing-deployment-history
  - /actions/deployment/viewing-deployment-history
  - /actions/deployment/managing-your-deployments/viewing-deployment-history
  - /actions/managing-workflow-runs-and-deployments/managing-deployments/viewing-deployment-history
  - /actions/how-tos/managing-workflow-runs-and-deployments/managing-deployments/viewing-deployment-history
---

## Viewing your repository's deployment history

On the deployments page of your repository, you can view the following aspects of your deployments.

* Currently active deployments across various environments
* Deployments filtered by environment
* Your repository's full deployment history
* Associated commits that triggered the deployment
* Connected {% data variables.product.prodname_actions %} workflow logs
* The deployment URL (if one exists)
* The source pull request and branch related to each deployment
* Deployment statuses. For more information about deployment statuses, see [AUTOTITLE](/rest/deployments/deployments#about-deployments).

By default, the deployments page shows currently active deployments from select environments and a timeline of the latest deployments for all environments.

1. In the right-hand sidebar of the home page of your repository, click **Deployments**.
1. Once you are on the "Deployments" page, you can view the following information about your deployment history.
   * **To view recent deployments for a specific environment**, in the "Environments" section of the left sidebar, click an environment.
   * **To pin an environment to the top of the deployment history list**, repository administrators can click {% octicon "pin" aria-label="Pin environment" %} to the right of the environment. You can pin up to ten environments.
   * **To view the commit that triggered a deployment**, in the deployment history list, click the commit message for the deployment you want to view.
      >[!NOTE]Deployments from commits that originate from a fork outside of the repository will not show links to the source pull request and branch related to each deployment. For more information about forks, see [AUTOTITLE](/pull-requests/collaborating-with-pull-requests/working-with-forks/about-forks).
   * **To view the URL for a deployment**, to the right of the commit message in the deployment history list, click {% octicon "link-external" aria-label="Navigate to deployment URL" %}.
   * **To navigate to the workflow run logs associated with a deployment**, to the right of the commit message in the deployment history list, click {% octicon "kebab-horizontal" aria-label="View logs" %}, then click **View logs**.
1. Optionally, to filter the deployment history list, create a filter.
   1. Click on the **{% octicon "filter" aria-hidden="true" aria-label="filter" %} Filter** button.
   1. Click **{% octicon "plus" aria-hidden="true" aria-label="plus" %} Add a filter**.
   1. Choose a qualifier you would like to filter the deployment history by.
   1. Depending on the qualifier you chose, fill out information in the "Operator" and "Value" columns.
   1. Optionally, click **{% octicon "plus" aria-hidden="true" aria-label="plus" %} Add a filter** to add another filter.
   1. Click **Apply**.
