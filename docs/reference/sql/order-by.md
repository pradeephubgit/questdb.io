---
title: ORDER BY keyword
sidebar_label: ORDER BY
description: ORDER BY SQL keyword reference documentation.
---

Sort the results of a query in ascending or descending order.

## Syntax

![Flow chart showing the syntax of the ORDER BY keyword](/img/docs/diagrams/orderBy.svg)

By default, the order is `ASC`. If you don't specify any order, the results are displayed in ascending order.

## Examples

```questdb-sql title="Omitting ASC will default to ascending order"
ratings ORDER BY userId;
```

```questdb-sql title="Ordering in descending order"
ratings ORDER BY userId DESC;
```

```questdb-sql title="Multi-level ordering"
ratings ORDER BY userId, rating DESC;
```

## Resource management

:::caution

Since ordering requires holding the data in RAM, check if you have sufficient memory
when performing large operations.

:::
