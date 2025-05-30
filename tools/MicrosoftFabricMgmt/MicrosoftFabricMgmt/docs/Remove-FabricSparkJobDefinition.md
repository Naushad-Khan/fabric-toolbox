# Remove-FabricSparkJobDefinition

## Overview

Deletes a SparkJobDefinition from a specified workspace in Microsoft Fabric.

## Features

- Sends a DELETE request to remove the SparkJobDefinition.
- Validates token expiration before making the API request.
- Logs detailed messages for debugging and error handling.

## Parameters

### WorkspaceId *(Mandatory)*

- **Description:** The unique identifier of the workspace containing the SparkJobDefinition to delete.
- **Type:** String

### SparkJobDefinitionId *(Mandatory)*

- **Description:** The unique identifier of the SparkJobDefinition to be deleted.
- **Type:** String

## Usage Examples

### Example 1: Removing a SparkJobDefinition

```powershell
$workspace = Get-FabricWorkspace -WorkspaceName "workspace-12345"
Remove-FabricSparkJobDefinition -WorkspaceId $workspace.id -SparkJobDefinitionId "SparkJobDefinition-67890"
```

This example removes the SparkJobDefinition with ID `SparkJobDefinition-67890` from the workspace with name `workspace-12345`.

## Prerequisites

- Use the command `Set-FabricApiHeaders` to set the global configuration variable `$FabricConfig`, containing:
  - `BaseUrl`: Base API endpoint for Fabric.
  - `FabricHeaders`: Authentication headers for API requests.
- Token validation requires the `Test-TokenExpired` helper function.

## Key Workflow

1. Validates the authentication token's validity using `Test-TokenExpired`.
2. Constructs the API URL for the DELETE request using the provided parameters.
3. Sends the DELETE request to remove the specified SparkJobDefinition.
4. Logs detailed responses and errors for debugging purposes.

## Error Handling

- Logs descriptive error messages if the API request fails or invalid input is detected.
- Returns `null` if an error occurs during execution.

## Author

**Tiago Balabuch**