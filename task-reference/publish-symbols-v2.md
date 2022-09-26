---
title: PublishSymbols@2 - Index sources and publish symbols v2 task
description: Index your source code and publish symbols to a file share or Azure Artifacts symbol server.
ms.date: 09/26/2022
monikerRange: "<=azure-pipelines"
---

# PublishSymbols@2 - Index sources and publish symbols v2 task

<!-- :::description::: -->
:::moniker range=">=azure-pipelines-2019.1"

<!-- :::editable-content name="description"::: -->
Index your source code and publish symbols to a file share or Azure Artifacts symbol server.
<!-- :::editable-content-end::: -->

:::moniker-end

:::moniker range="=azure-pipelines-2019"

<!-- :::editable-content name="description"::: -->
Index your source code and publish symbols to a file share or Azure Artifacts Symbol Server.
<!-- :::editable-content-end::: -->

:::moniker-end

:::moniker range="=azure-pipelines-2018"

<!-- :::editable-content name="description"::: -->
Index your source code and publish symbols to a file share or Visual Studio Team Services Symbol Server.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::description-end::: -->

<!-- :::syntax::: -->
## Syntax

:::moniker range=">=azure-pipelines-2022"

```yaml
# Index sources and publish symbols v2
# Index your source code and publish symbols to a file share or Azure Artifacts symbol server.
- task: PublishSymbols@2
  inputs:
    #SymbolsFolder: '$(Build.SourcesDirectory)' # string. Path to symbols folder. Default: $(Build.SourcesDirectory).
    SearchPattern: '**/bin/**/*.pdb' # string. Required. Search pattern. Default: **/bin/**/*.pdb.
    #IndexSources: true # boolean. Index sources. Default: true.
    #PublishSymbols: true # boolean. Publish symbols. Default: true.
    SymbolServerType: # 'TeamServices' | 'FileShare'. Required when PublishSymbols = true. Symbol server type. 
    #SymbolsPath: # string. Optional. Use when PublishSymbols = true && SymbolServerType = FileShare. Path to publish symbols. 
    #CompressSymbols: false # boolean. Required when SymbolServerType = FileShare. Compress symbols. Default: false.
    #SymbolExpirationInDays: '36530' # string. Optional. Use when PublishSymbols = true && SymbolServerType = TeamServices. Symbol Expiration (in days). Default: 36530.
  # Advanced
    #IndexableFileFormats: 'Default' # 'Default' | 'Pdb' | 'SourceMap' | 'All'. Optional. Use when PublishSymbols = true && SymbolServerType = TeamServices. Symbol file formats to publish. Default: Default.
    #DetailedLog: true # boolean. Verbose logging. Default: true.
    #TreatNotIndexedAsWarning: false # boolean. Warn if not indexed. Default: false.
    #UseNetCoreClientTool: false # boolean. Use NetCore client tool. Default: false.
    #SymbolsMaximumWaitTime: # string. Max wait time (min). 
    #SymbolsProduct: # string. Product. 
    #SymbolsVersion: # string. Version. 
    #SymbolsArtifactName: 'Symbols_$(BuildConfiguration)' # string. Artifact name. Default: Symbols_$(BuildConfiguration).
```

:::moniker-end

:::moniker range=">=azure-pipelines-2019.1 <=azure-pipelines-2020.1"

```yaml
# Index sources and publish symbols v2
# Index your source code and publish symbols to a file share or Azure Artifacts symbol server.
- task: PublishSymbols@2
  inputs:
    #SymbolsFolder: '$(Build.SourcesDirectory)' # string. Path to symbols folder. Default: $(Build.SourcesDirectory).
    SearchPattern: '**/bin/**/*.pdb' # string. Required. Search pattern. Default: **/bin/**/*.pdb.
    #IndexSources: true # boolean. Index sources. Default: true.
    #PublishSymbols: true # boolean. Publish symbols. Default: true.
    SymbolServerType: # 'TeamServices' | 'FileShare'. Required when PublishSymbols = true. Symbol server type. 
    #SymbolsPath: # string. Optional. Use when PublishSymbols = true && SymbolServerType = FileShare. Path to publish symbols. 
    #CompressSymbols: false # boolean. Required when SymbolServerType = FileShare. Compress symbols. Default: false.
  # Advanced
    #DetailedLog: true # boolean. Verbose logging. Default: true.
    #TreatNotIndexedAsWarning: false # boolean. Warn if not indexed. Default: false.
    #SymbolsMaximumWaitTime: # string. Max wait time (min). 
    #SymbolsProduct: # string. Product. 
    #SymbolsVersion: # string. Version. 
    #SymbolsArtifactName: 'Symbols_$(BuildConfiguration)' # string. Artifact name. Default: Symbols_$(BuildConfiguration).
```

:::moniker-end

:::moniker range="=azure-pipelines-2019"

```yaml
# Index sources and publish symbols v2
# Index your source code and publish symbols to a file share or Azure Artifacts Symbol Server.
- task: PublishSymbols@2
  inputs:
    #SymbolsFolder: '$(Build.SourcesDirectory)' # string. Path to symbols folder. Default: $(Build.SourcesDirectory).
    SearchPattern: '**/bin/**/*.pdb' # string. Required. Search pattern. Default: **/bin/**/*.pdb.
    #IndexSources: true # boolean. Index sources. Default: true.
    #PublishSymbols: true # boolean. Publish symbols. Default: true.
    SymbolServerType: # 'TeamServices' | 'FileShare'. Required when PublishSymbols = true. Symbol server type. 
    #SymbolsPath: # string. Optional. Use when PublishSymbols = true && SymbolServerType = FileShare. Path to publish symbols. 
    #CompressSymbols: false # boolean. Required when SymbolServerType = FileShare. Compress symbols. Default: false.
  # Advanced
    #DetailedLog: true # boolean. Verbose logging. Default: true.
    #TreatNotIndexedAsWarning: false # boolean. Warn if not indexed. Default: false.
    #SymbolsMaximumWaitTime: # string. Max wait time (min). 
    #SymbolsProduct: # string. Product. 
    #SymbolsVersion: # string. Version. 
    #SymbolsArtifactName: 'Symbols_$(BuildConfiguration)' # string. Artifact name. Default: Symbols_$(BuildConfiguration).
```

:::moniker-end

:::moniker range="=azure-pipelines-2018"

```yaml
# YAML Syntax is not supported in TFS 2018.
# Use the classic designer to add and configure tasks.
# See the following Inputs section for details on the inputs that this task supports.
```

:::moniker-end
<!-- :::syntax-end::: -->

<!-- :::inputs::: -->
## Inputs

<!-- :::item name="SymbolsFolder"::: -->
:::moniker range="<=azure-pipelines"

**`SymbolsFolder`** - **Path to symbols folder**<br>
`string`. Default value: `$(Build.SourcesDirectory)`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
The path to the folder that is searched for symbol files.  The default is $(Build.SourcesDirectory).  Otherwise specify a rooted path, for example: $(Build.BinariesDirectory)/MyProject.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="SearchPattern"::: -->
:::moniker range="<=azure-pipelines"

**`SearchPattern`** - **Search pattern**<br>
`string`. Required. Default value: `**/bin/**/*.pdb`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
The pattern used to discover the pdb files to publish.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="IndexSources"::: -->
:::moniker range="<=azure-pipelines"

**`IndexSources`** - **Index sources**<br>
`boolean`. Default value: `true`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Indicates whether to inject source server information into the PDB files.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="PublishSymbols"::: -->
:::moniker range="<=azure-pipelines"

**`PublishSymbols`** - **Publish symbols**<br>
`boolean`. Default value: `true`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Indicates whether to publish the symbol files.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="SymbolServerType"::: -->
:::moniker range=">=azure-pipelines-2019"

**`SymbolServerType`** - **Symbol server type**<br>
`string`. Required when `PublishSymbols = true`. Allowed values: `TeamServices` (Symbol Server in this organization/collection (requires Azure Artifacts)), `FileShare` (File share).<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Choose where to publish symbols. Symbols published to the Azure Artifacts symbol server are accessible by any user with access to the organization/collection. Azure DevOps Server only supports the "File share" option. Follow [these instructions](https://go.microsoft.com/fwlink/?linkid=846265) to use Symbol Server in Azure Artifacts.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end

:::moniker range="=azure-pipelines-2018"

**`SymbolServerType`** - **Symbol server type**<br>
`string`. Required when `PublishSymbols = true`. Allowed values: `TeamServices` (Symbol Server in this account/collection (requires Package Management)), `FileShare` (File share).<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Choose where to publish symbols. Symbols published to the Azure Artifacts symbol server are accessible by any user with access to the organization/collection. Azure DevOps Server only supports the "File share" option. Follow [these instructions](https://go.microsoft.com/fwlink/?linkid=846265) to use Symbol Server in Azure Artifacts.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="SymbolsPath"::: -->
:::moniker range="<=azure-pipelines"

**`SymbolsPath`** - **Path to publish symbols**<br>
`string`. Optional. Use when `PublishSymbols = true && SymbolServerType = FileShare`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
The file share that hosts your symbols. This value will be used in the call to `symstore.exe add` as the `/s` parameter.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="CompressSymbols"::: -->
:::moniker range=">=azure-pipelines-2019"

**`CompressSymbols`** - **Compress symbols**<br>
`boolean`. Required when `SymbolServerType = FileShare`. Default value: `false`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Compress symbols when publishing to file share.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="SymbolExpirationInDays"::: -->
:::moniker range=">=azure-pipelines-2022"

**`SymbolExpirationInDays`** - **Symbol Expiration (in days)**<br>
`string`. Optional. Use when `PublishSymbols = true && SymbolServerType = TeamServices`. Default value: `36530`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
The number of days that symbols should be retained.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="IndexableFileFormats"::: -->
:::moniker range=">=azure-pipelines-2022"

**`IndexableFileFormats`** - **Symbol file formats to publish**<br>
`string`. Optional. Use when `PublishSymbols = true && SymbolServerType = TeamServices`. Allowed values: `Default` (The Default set of symbols to upload), `Pdb` (Only Pdb based symbols Windows pdb's and managed Portable pdb's.), `SourceMap` (Only JavaScript based SourceMap symbols (*.js.map)), `All` (All supported symbol formats). Default value: `Default`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Which debug formats to publish to the symbol server.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="DetailedLog"::: -->
:::moniker range="<=azure-pipelines"

**`DetailedLog`** - **Verbose logging**<br>
`boolean`. Default value: `true`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Use verbose logging.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="TreatNotIndexedAsWarning"::: -->
:::moniker range="<=azure-pipelines"

**`TreatNotIndexedAsWarning`** - **Warn if not indexed**<br>
`boolean`. Default value: `false`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Indicates whether to warn if sources are not indexed for a PDB file. Otherwise the messages are logged as normal output.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="UseNetCoreClientTool"::: -->
:::moniker range=">=azure-pipelines-2022"

**`UseNetCoreClientTool`** - **Use NetCore client tool**<br>
`boolean`. Default value: `false`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Indicates whether to use version of the symbol upload tool that supports DWARF and ELF files. This option only matters on Windows agents. On non-Windows agents, the version of the symbol upload tool that supports DWARF and ELF files will always be used.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="SymbolsMaximumWaitTime"::: -->
:::moniker range="<=azure-pipelines"

**`SymbolsMaximumWaitTime`** - **Max wait time (min)**<br>
`string`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
The number of minutes to wait before failing this task.
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="SymbolsProduct"::: -->
:::moniker range="<=azure-pipelines"

**`SymbolsProduct`** - **Product**<br>
`string`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the product parameter to symstore.exe.  The default is $(Build.DefinitionName).
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="SymbolsVersion"::: -->
:::moniker range="<=azure-pipelines"

**`SymbolsVersion`** - **Version**<br>
`string`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the version parameter to symstore.exe.  The default is $(Build.BuildNumber).
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="SymbolsArtifactName"::: -->
:::moniker range="<=azure-pipelines"

**`SymbolsArtifactName`** - **Artifact name**<br>
`string`. Default value: `Symbols_$(BuildConfiguration)`.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the artifact name to use for the Symbols artifact.  The default is Symbols_$(BuildConfiguration).
<!-- :::editable-content-end::: -->
<br>

:::moniker-end
<!-- :::item-end::: -->

### Task control options

All tasks have control options in addition to their task inputs. For more information, see [Control options and common task properties](/azure/devops/pipelines/yaml-schema/steps-task#common-task-properties).
<!-- :::inputs-end::: -->

<!-- :::outputVariables::: -->
## Output variables

:::moniker range="<=azure-pipelines"

None.

:::moniker-end
<!-- :::outputVariables-end::: -->

<!-- :::remarks::: -->
<!-- :::editable-content name="remarks"::: -->
## Remarks

Use this task to index your source code and publish your symbols to a file share or Azure Artifacts symbol server.

Indexing your source code allows you to use your symbol files to debug your application on a machine other than the one you used to build your application. For example, you can debug an application built by a build agent from a dev machine that does not have the source code.

Symbol servers enables your debugger to automatically retrieve the correct symbol files without knowing product names, build numbers, or package names.

> [!IMPORTANT]
> To delete symbols that were published using the *Index Sources & Publish Symbols* task, you must first delete the build that generated those symbols. This can be accomplished by using [retention policies](/azure/devops/pipelines/build/ci-build-git#use-retention-policies-to-clean-up-your-completed-builds) or by manually [deleting the run](/azure/devops/pipelines/policies/retention#delete-a-run).

### How does indexing work?

By choosing to index the sources, an extra section will be injected into the PDB files. PDB files normally contain references to the local source file paths only E.g: *C:\BuildAgent\_work\1\src\MyApp\Program.cs*. The extra section injected into the PDB file contains mapping instructions for debuggers. The mapping information indicates how to retrieve the server item corresponding to each local path.

 The Visual Studio debugger will use the mapping information to retrieve the source file from the server. An actual command to retrieve the source file is included in the mapping information. Example:

```command
tf.exe git view /collection:http://SERVER:8080/tfs/DefaultCollection /teamproject:"93fc2e4d-0f0f-4e40-9825-01326191395d" /repository:"647ed0e6-43d2-4e3d-b8bf-2885476e9c44" /commitId:3a9910862e22f442cd56ff280b43dd544d1ee8c9 /path:"/MyApp/Program.cs" /output:"C:\Users\username\AppData\Local\SOURCE~1\TFS_COMMIT\3a991086\MyApp\Program.cs" /applyfilters
```

### Can I use source indexing on a portable PDB created from a .NET Core assembly?

No, but you can use [Source Link](/dotnet/standard/library-guidance/sourcelink) instead.

### How long are Symbols retained?

Symbols are associated with the build that published to Azure Pipelines they are associated with a build. When the build is deleted either manually or using retention policies, the symbols are also deleted. If you want to retain the symbols indefinitely, mark the build as **Retain Indefinitely**.
<!-- :::editable-content-end::: -->
<!-- :::remarks-end::: -->

<!-- :::examples::: -->
<!-- :::editable-content name="examples"::: -->
<!-- :::editable-content-end::: -->
<!-- :::examples-end::: -->

<!-- :::properties::: -->
## Requirements

:::moniker range=">=azure-pipelines-2022"

| Requirement | Description |
|-------------|-------------|
| Pipeline types | YAML, Classic build |
| Runs on | Agent, DeploymentGroup |
| [Demands](/azure/devops/pipelines/process/demands) | None |
| [Capabilities](/azure/devops/pipelines/agents/agents#capabilities) | This task does not satisfy any demands for subsequent tasks in the job. |
| [Command restrictions](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| [Settable variables](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| Agent version |  2.144.0 or greater |
| Task category | Build |

:::moniker-end

:::moniker range="<=azure-pipelines-2020.1"

| Requirement | Description |
|-------------|-------------|
| Pipeline types | YAML, Classic build |
| Runs on | Agent, DeploymentGroup |
| [Demands](/azure/devops/pipelines/process/demands) | None |
| [Capabilities](/azure/devops/pipelines/agents/agents#capabilities) | This task does not satisfy any demands for subsequent tasks in the job. |
| [Command restrictions](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| [Settable variables](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| Agent version |  1.95.0 or greater |
| Task category | Build |

:::moniker-end
<!-- :::properties-end::: -->

<!-- :::see-also::: -->
<!-- :::editable-content name="seeAlso"::: -->
## See also

* [Publish symbols for debugging](/azure/devops/pipelines/artifacts/symbols)
* [Debug with Visual Studio](/azure/devops/artifacts/symbols/debug-with-symbols-visual-studio)
* [Debug with WinDbg](/azure/devops/artifacts/symbols/debug-with-symbols-windbg)
<!-- :::editable-content-end::: -->
<!-- :::see-also-end::: -->