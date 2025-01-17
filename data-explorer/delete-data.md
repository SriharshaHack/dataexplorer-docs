---
title: Delete data from Azure Data Explorer
description: This article describes delete scenarios in Azure Data Explorer, including purge, dropping extents and retention based deletes.
author: orspod
ms.author: orspodek
ms.reviewer: avneraa
ms.service: data-explorer
ms.topic: how-to
ms.date: 03/12/2020
---

# Delete data from Azure Data Explorer

Azure Data Explorer supports various delete scenarios described in this article. 

## Delete data using the retention policy

Azure Data Explorer automatically deletes data based on the [retention policy](kusto/management/retentionpolicy.md). This method is the most efficient and hassle-free way of deleting data. Set the retention policy at the database or table level.

Consider a database or table that is set for 90 days of retention. If only 60 days of data are needed, delete the older data as follows:

```kusto
.alter-merge database <DatabaseName> policy retention softdelete = 60d

.alter-merge table <TableName> policy retention softdelete = 60d
```

## Delete data by dropping extents

[Extent (data shard)](kusto/management/extents-overview.md) is the internal structure where data is stored. Each extent can hold up to millions of records. Extents can be deleted individually or as a group using [drop extent(s) commands](./kusto/management/drop-extents.md).

### Examples

You can delete all rows in a table or just a specific extent.

* Delete all rows in a table:

    ```kusto
    .drop extents from TestTable
    ```

* Delete a specific extent:

    ```kusto
    .drop extent e9fac0d2-b6d5-4ce3-bdb4-dea052d13b42
    ```

## Delete individual rows

Both purge and soft-delete can be used for deleting individuals rows, but they are designed for completely different scenarios.

### Purge

With [purge](kusto/concepts/data-purge.md), all storage artifacts that have "poison" data is deleted. The deletion isn't immediate and requires significant system resources. As such, it's only recommended for compliance scenarios.

### Soft-delete

With [soft-delete](kusto/concepts/data-soft-delete.md), data is not necessarily deleted from storage artifacts and, as such, it cannot be used for compliance scenarios. The deletion is immediate and doesn't require significant system resources.
