# Workflow for Using this Template

## Creating New Project

1. Execute copier to lay down the template
1. Edit `src/CHART-NAME-HERE/Chart.yaml` to set the value of `appVersion` as appropriate for your chart
   - Note you do _not_ have to set the `version` value, as the Helm chart will be automatically versioned via commit-and-tag-version
1. Edit the rest of the Helm chart as appropriate. The files inside `src/CHART-NAME-HERE` are the default output of `helm create`.

### Registry Type

#### Azure Container Registry

##### If Using Auth Mode 'Admin Credentials via Pipeline Variable'

1. In the Azure Portal, open the ACR, then go to `Settings > Access keys`
1. Make sure `Admin user` is checked, then copy the value for `password`
1. In Azure DevOps, open and edit the pipeline
1. Click the Variables button, then create a variable as follows:
   - Name: `AcrPasswordSecret`
   - Value: The password you copied above
   - Keep this value secret: `Checked`
1. Click OK, then Save

## Applying to Existing Project

To apply this template to an existing project, follow these steps:

1. Ensure your project is already using Git, and the all of the following are true:
   1. Project is cloned out to your local computer
   1. All changes are committed
   1. Default branch (usually `main` or `master`) is checked out
1. Create a new branch (`copier-template-apply`, for example) from your default branch
1. Make sure your shell is in the project root, then run the following in order to apply the template to your local project:

   ```shell
    copier copy --trust --overwrite gh:natescherer/postmodern-helm-chart-copiertemplate .
   ```

1. If you are using GitHub, Make sure to choose `Set Repo Rules` in the first question
1. Set all other settings as appropriate for your project
1. Once the template is applied, review files that have been changed using git, and stage, discard, or modify as appropriate
1. Commit and push the changes, then merge them via a Pull Request
1. You are done, and your project will now operate the same as one that was generated from this template.

## Updating Existing Project to New Template Version

Coming Soon
