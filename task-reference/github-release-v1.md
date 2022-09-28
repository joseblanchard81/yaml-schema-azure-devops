---
title: GitHubRelease@1 - GitHub Release v1 task
description: Create, edit, or delete a GitHub release.
ms.date: 09/26/2022
monikerRange: ">=azure-pipelines-2020"
---

# GitHubRelease@1 - GitHub Release v1 task

<!-- :::description::: -->
:::moniker range=">=azure-pipelines-2020"

<!-- :::editable-content name="description"::: -->
Create, edit, or delete a GitHub release.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::description-end::: -->

<!-- :::syntax::: -->
## Syntax

:::moniker range=">=azure-pipelines-2020"

```yaml
# GitHub Release v1
# Create, edit, or delete a GitHub release.
- task: GitHubRelease@1
  inputs:
    gitHubConnection: # string. Required. GitHub connection (OAuth or PAT). 
    repositoryName: '$(Build.Repository.Name)' # string. Required. Repository. Default: $(Build.Repository.Name).
    action: 'create' # 'create' | 'edit' | 'delete'. Required. Action. Default: create.
    #target: '$(Build.SourceVersion)' # string. Required when action = create || action = edit. Target. Default: $(Build.SourceVersion).
    tagSource: 'gitTag' # 'gitTag' | 'userSpecifiedTag'. Required when action = create. Tag source. Default: gitTag.
    #tagPattern: # string. Optional. Use when tagSource = gitTag. Tag Pattern. 
    #tag: # string. Required when action = edit || action = delete || tagSource = userSpecifiedTag. Tag. 
    #title: # string. Optional. Use when action = create || action = edit. Release title. 
    #releaseNotesSource: 'filePath' # 'filePath' | 'inline'. Optional. Use when action = create || action = edit. Release notes source. Default: filePath.
    #releaseNotesFilePath: # string. Optional. Use when releaseNotesSource = filePath. Release notes file path. 
    #releaseNotesInline: # string. Optional. Use when releaseNotesSource = inline. Release notes. 
    #assets: '$(Build.ArtifactStagingDirectory)/*' # string. Optional. Use when action = create || action = edit. Assets. Default: $(Build.ArtifactStagingDirectory)/*.
    #assetUploadMode: 'delete' # 'delete' | 'replace'. Optional. Use when action = edit. Asset upload mode. Default: delete.
    #isDraft: false # boolean. Optional. Use when action = create || action = edit. Draft release. Default: false.
    #isPreRelease: false # boolean. Optional. Use when action = create || action = edit. Pre-release. Default: false.
    #addChangeLog: true # boolean. Optional. Use when action = create || action = edit. Add changelog. Default: true.
  # Changelog configuration
    changeLogCompareToRelease: 'lastFullRelease' # 'lastFullRelease' | 'lastNonDraftRelease' | 'lastNonDraftReleaseByTag'. Required when addChangeLog = true. Compare to. Default: lastFullRelease.
    #changeLogCompareToReleaseTag: # string. Required when changeLogCompareToRelease = lastNonDraftReleaseByTag. Release Tag. 
    changeLogType: 'commitBased' # 'commitBased' | 'issueBased'. Required when addChangeLog = true. Changelog type. Default: commitBased.
    #changeLogLabels: '[{ "label" : "bug", "displayName" : "Bugs", "state" : "closed" }]' # string. Optional. Use when changeLogType = issueBased. Categories. Default: [{ "label" : "bug", "displayName" : "Bugs", "state" : "closed" }].
```

:::moniker-end
<!-- :::syntax-end::: -->

<!-- :::inputs::: -->
## Inputs

<!-- :::item name="gitHubConnection"::: -->
:::moniker range=">=azure-pipelines-2020"

**`gitHubConnection`** - **GitHub connection (OAuth or PAT)**<br>
`string`. Required.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the name of the GitHub service connection to use to connect to the GitHub repository. The connection must be based on a GitHub user's OAuth or a GitHub personal access token. Learn more about [service connections](/azure/devops/pipelines/library/service-endpoints#sep-github).
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="repositoryName"::: -->
:::moniker range=">=azure-pipelines-2020"

**`repositoryName`** - **Repository**<br>
`string`. Required. Default value: `$(Build.Repository.Name)`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the name of the GitHub repository in which the GitHub release will be created, edited, or deleted.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="action"::: -->
:::moniker range=">=azure-pipelines-2020"

**`action`** - **Action**<br>
`string`. Required. Allowed values: `create`, `edit`, `delete`. Default value: `create`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the type of release operation to perform. This task can create, edit, or delete a GitHub release.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="target"::: -->
:::moniker range=">=azure-pipelines-2020"

**`target`** - **Target**<br>
`string`. Required when `action = create || action = edit`. Default value: `$(Build.SourceVersion)`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the commit SHA for which the GitHub release will be created (for example: `48b11d8d6e92a22e3e9563a3f643699c16fd6e27`). You can also use a variable here (for example: `$(myCommitSHA)`).
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="tagSource"::: -->
:::moniker range=">=azure-pipelines-2020"

**`tagSource`** - **Tag source**<br>
`string`. Required when `action = create`. Allowed values: `gitTag` (Git tag), `userSpecifiedTag` (User specified tag). Default value: `gitTag`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the tag to be used for release creation. The `Git tag` option automatically takes the tag which is associated with the Git commit. Use the `User specified tag` option to manually provide a tag.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="tagPattern"::: -->
:::moniker range=">=azure-pipelines-2020"

**`tagPattern`** - **Tag Pattern**<br>
`string`. Optional. Use when `tagSource = gitTag`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the git tag pattern using regex (for example: `release-v1.*`). GitHub release will be created only for commits that have matching git tag.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="tag"::: -->
:::moniker range=">=azure-pipelines-2020"

**`tag`** - **Tag**<br>
`string`. Required when `action = edit || action = delete || tagSource = userSpecifiedTag`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the tag for which to create, edit, or delete a release. You can also use a variable here (for example: `$(myTagName)`).
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="title"::: -->
:::moniker range=">=azure-pipelines-2020"

**`title`** - **Release title**<br>
`string`. Optional. Use when `action = create || action = edit`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the title of the GitHub release. If left empty, the tag will be used as the release title.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="releaseNotesSource"::: -->
:::moniker range=">=azure-pipelines-2020"

**`releaseNotesSource`** - **Release notes source**<br>
`string`. Optional. Use when `action = create || action = edit`. Allowed values: `filePath` (Release notes file), `inline` (Inline release notes). Default value: `filePath`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the description of the GitHub release. Use the `Release notes file` option to use the contents of a file as release notes. Use the `Inline release notes` option to manually enter release notes.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="releaseNotesFilePath"::: -->
:::moniker range=">=azure-pipelines-2020"

**`releaseNotesFilePath`** - **Release notes file path**<br>
`string`. Optional. Use when `releaseNotesSource = filePath`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Select the file which contains the release notes.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="releaseNotesInline"::: -->
:::moniker range=">=azure-pipelines-2020"

**`releaseNotesInline`** - **Release notes**<br>
`string`. Optional. Use when `releaseNotesSource = inline`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Enter the release notes here. Markdown is supported.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="assets"::: -->
:::moniker range=">=azure-pipelines-2020"

**`assets`** - **Assets**<br>
`string`. Optional. Use when `action = create || action = edit`. Default value: `$(Build.ArtifactStagingDirectory)/*`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the files to be uploaded as assets of the release. You can use wildcard characters to specify multiple files. E.g. For build pipelines, `$(Build.ArtifactStagingDirectory)/*.zip` or in case of release pipelines `$(System.DefaultWorkingDirectory)/*.zip`. You can also specify multiple patterns - one per line. By default, all files in the `$(Build.ArtifactStagingDirectory)` directory will be uploaded. To know more about the list of pre-defined variables available, see [build variables](/azure/devops/pipelines/build/variables) and [release variables](/azure/devops/pipelines/release/variables#system-variables).
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="assetUploadMode"::: -->
:::moniker range=">=azure-pipelines-2020"

**`assetUploadMode`** - **Asset upload mode**<br>
`string`. Optional. Use when `action = edit`. Allowed values: `delete` (Delete exisiting assets), `replace` (Replace existing assets). Default value: `delete`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Use the `Delete existing assets` option to first delete any existing assets in the release and then upload all assets. Use the `Replace existing assets` option to replace any assets that have the same name.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="isDraft"::: -->
:::moniker range=">=azure-pipelines-2020"

**`isDraft`** - **Draft release**<br>
`boolean`. Optional. Use when `action = create || action = edit`. Default value: `false`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Indicate whether the release should be saved as a draft (unpublished). If `false`, the release will be published.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="isPreRelease"::: -->
:::moniker range=">=azure-pipelines-2020"

**`isPreRelease`** - **Pre-release**<br>
`boolean`. Optional. Use when `action = create || action = edit`. Default value: `false`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Indicate whether the release should be marked as a pre-release.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="addChangeLog"::: -->
:::moniker range=">=azure-pipelines-2020"

**`addChangeLog`** - **Add changelog**<br>
`boolean`. Optional. Use when `action = create || action = edit`. Default value: `true`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
If set to `true`, a list of changes (commits and issues) between this and the last published release will be generated and appended to the release notes.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="changeLogCompareToRelease"::: -->
:::moniker range=">=azure-pipelines-2020"

**`changeLogCompareToRelease`** - **Compare to**<br>
`string`. Required when `addChangeLog = true`. Allowed values: `lastFullRelease` (Last full release), `lastNonDraftRelease` (Last non-draft release), `lastNonDraftReleaseByTag` (Last non-draft release by tag). Default value: `lastFullRelease`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Indicate which release we should compare with to generate the changelog: 
Last full release: Compares the current release with  the most recent non-draft release which is not marked as pre-release.
Last non-draft release: Compares the current release with the most recent non-draft release.
Last non-draft release by tag: Compares the current release with the last non-draft release matching the specified tag. You can also specify a regex instead of an exact tag.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="changeLogCompareToReleaseTag"::: -->
:::moniker range=">=azure-pipelines-2020"

**`changeLogCompareToReleaseTag`** - **Release Tag**<br>
`string`. Required when `changeLogCompareToRelease = lastNonDraftReleaseByTag`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the regex for release tag. Release matching this tag will be used as base for changelog computation.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="changeLogType"::: -->
:::moniker range=">=azure-pipelines-2020"

**`changeLogType`** - **Changelog type**<br>
`string`. Required when `addChangeLog = true`. Allowed values: `commitBased` (Commit based), `issueBased` (Issue based). Default value: `commitBased`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Changelog can be commit based or issue based . Commit based changelog lists all commits included in a release where as Issue based changelog lists all the issues/pr included in the release.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="changeLogLabels"::: -->
:::moniker range=">=azure-pipelines-2020"

**`changeLogLabels`** - **Categories**<br>
`string`. Optional. Use when `changeLogType = issueBased`. Default value: `[{ "label" : "bug", "displayName" : "Bugs", "state" : "closed" }]`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Using this you can categorize changes based on the label associated with the issue/pr. For a label you can mention the display name for the category and the state of issue. E.g. `"[{ "label" : "bug", "displayName" : "Bugs", "state" : "closed" }]"` .In case a change has multiple labels on it, the first specified label takes priority. Leave this field empty, to see a flat list of issues/pr.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->

### Task control options

All tasks have control options in addition to their task inputs. For more information, see [Control options and common task properties](/azure/devops/pipelines/yaml-schema/steps-task#common-task-properties).
<!-- :::inputs-end::: -->

<!-- :::outputVariables::: -->
## Output variables

:::moniker range=">=azure-pipelines-2020"

None.

:::moniker-end
<!-- :::outputVariables-end::: -->

<!-- :::remarks::: -->
<!-- :::editable-content name="remarks"::: -->
## Remarks

Use this task in your pipeline to create, edit, or discard a [GitHub release](https://help.github.com/categories/releases/).

### GitHub service connection
This task requires a [GitHub service connection](/azure/devops/pipelines/library/service-endpoints#github-service-connection) with **Write** permission to the GitHub repository. You can create a GitHub service connection in your Azure Pipelines project. Once created, use the name of the service connection in this task's settings.
<!-- :::editable-content-end::: -->
<!-- :::remarks-end::: -->

<!-- :::examples::: -->
<!-- :::editable-content name="examples"::: -->
## Examples

### Create a GitHub release

The following YAML creates a GitHub release every time the task runs. The build number is used as the tag version for the release. All .exe files and README.txt files in the $(Build.ArtifactStagingDirectory) folder are uploaded as assets. By default, the task also generates a change log (a list of commits and issues that are part of this release) and publishes it as release notes.

```YAML
- task: GithubRelease@1 
  displayName: 'Create GitHub Release'      
  inputs:
    gitHubConnection: zenithworks
    repositoryName: zenithworks/javaAppWithMaven
    tagSource: manual
    tag: $(Build.BuildNumber)      
    assets: |
      $(Build.ArtifactStagingDirectory)/*.exe
      $(Build.ArtifactStagingDirectory)/README.txt
```

You can also control the creation of the release based on repository tags. The following YAML creates a GitHub release only when the commit that triggers the pipeline has a Git tag associated with it. The GitHub release is created with the same tag version as the associated Git tag.

```YAML
- task: GithubRelease@1 
  displayName: 'Create GitHub Release'      
  inputs:
    gitHubConnection: zenithworks
    repositoryName: zenithworks/javaAppWithMaven           
    assets: $(Build.ArtifactStagingDirectory)/*.exe
```

You may also want to use the task in conjunction with task conditions to get even finer control over when the task runs, thereby restricting the creation of releases. For example, in the following YAML the task runs only when the pipeline is triggered by a Git tag matching the pattern 'refs/tags/release-v*'.

```YAML
- task: GithubRelease@1 
  displayName: 'Create GitHub Release'   
  condition: startsWith(variables['Build.SourceBranch'], 'refs/tags/release-v')   
  inputs:
    gitHubConnection: zenithworks
    repositoryName: zenithworks/javaAppWithMaven           
    assets: $(Build.ArtifactStagingDirectory)/*.exe
```

### Edit a GitHub release

The following YAML updates the status of a GitHub release from 'draft' to 'published'. The release to be edited is determined by the specified tag.

```YAML
- task: GithubRelease@1
  displayName: 'Edit GitHub Release'
  inputs:
    gitHubConnection: zenithworks
    repositoryName: zenithworks/javaAppWithMaven
    action: edit
    tag: $(myDraftReleaseVersion)
    isDraft: false
```

### Delete a GitHub release

The following YAML deletes a GitHub release. The release to be deleted is determined by the specified tag.

```YAML
- task: GithubRelease@1
  displayName: 'Delete GitHub Release'
  inputs:
    gitHubConnection: zenithworks
    repositoryName: zenithworks/javaAppWithMaven
    action: delete
    tag: $(myDraftReleaseVersion)
```

### Inline release notes

The following YAML create a GitHub release and add inline release notes.

```YAML
- task: GitHubRelease@1
  inputs:
    gitHubConnection: <GITHUB_SERVICE_CONNECTION>
    repositoryName: '$(Build.Repository.Name)'
    action: 'create'
    target: '$(Build.SourceVersion)'
    tagSource: 'userSpecifiedTag'
    tag: <YOUR_TAG>
    title: <YOUR_TITLE>
    releaseNotesSource: 'inline'
    releaseNotesInline: <YOUR_RELEASE_NOTES>
```
<!-- :::editable-content-end::: -->
<!-- :::examples-end::: -->

<!-- :::properties::: -->
## Requirements

:::moniker range=">=azure-pipelines-2020"

| Requirement | Description |
|-------------|-------------|
| Pipeline types | YAML, Classic build, Classic release |
| Runs on | Agent, DeploymentGroup |
| [Demands](/azure/devops/pipelines/process/demands) | None |
| [Capabilities](/azure/devops/pipelines/agents/agents#capabilities) | This task does not satisfy any demands for subsequent tasks in the job. |
| [Command restrictions](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| [Settable variables](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| Agent version |  2.0.0 or greater |
| Task category | Utility |

:::moniker-end
<!-- :::properties-end::: -->

<!-- :::see-also::: -->
<!-- :::editable-content name="seeAlso"::: -->
<!-- :::editable-content-end::: -->
<!-- :::see-also-end::: -->