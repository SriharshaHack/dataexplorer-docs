---
title: Show query weak consistency policy management - Azure Data Explorer
description: This article describes the `.show query weak consistency policy` command in Azure Data Explorer.
services: data-explorer
author: orspod
ms.author: orspodek
ms.reviewer: yabenyaa
ms.service: data-explorer
ms.topic: reference
ms.date: 08/16/2021
---
# .show query weak consistency policy

This article describes the show control command used for the [query weak consistency policy](query-weak-consistency-policy.md). This command returns the query weak consistency policy of the cluster.

## Syntax

```kusto
.show cluster policy query_weak_consistency
```

## Output

|Policy name | Entity name | Policy | Child entities | Entity type
|---|---|---|---|---
|QueryWeakConsistencyPolicy |  | JSON serialization of the [query weak consistency policy object](./query-weak-consistency-policy.md#the-policy-object) | | Cluster

## Example

<!-- csl -->
```
.show cluster policy query_weak_consistency 
```

|PolicyName|EntityName|Policy|ChildEntities|EntityType|
|---|---|---|---|---|
|QueryWeakConsistencyPolicy||{"PercentageOfNodes": -1, "MinimumNumberOfNodes": -1, "EnableMetadataPrefetch": false, "MaximumLagAllowedInMinutes": -1, "RefreshPeriodInSeconds": -1}| |Cluster