---
title: .delete restricted view access policy command - Azure Data Explorer
description: This article describes the .delete restricted view access policy command in Azure Data Explorer.
services: data-explorer
author: orspod
ms.author: orspodek
ms.reviewer: yonil
ms.service: data-explorer
ms.topic: reference
ms.date: 09/27/2021
---
# .delete restricted view access policy

Delete the optional table [restricted view access policy](restrictedviewaccesspolicy.md). When this policy is enabled for a table, data in the table can only be queried by principals who have an [UnrestrictedViewer](../management/access-control/role-based-authorization.md) role in the database. Deleting a policy is similar to disabling a policy. 

## Syntax

`.delete` `table` *TableName* `policy` `restricted-view-access`

## Arguments

*TableName* - Specify the name of the table. 

## Example

```kusto
.delete table MyTable policy restricted-view-access
```
