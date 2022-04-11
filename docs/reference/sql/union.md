---
title: UNION keyword
sidebar_label: UNION
description: UNION SQL keyword reference documentation.
---

## Overview

`UNION` is used to combine the results of two or more `SELECT` statements. To
work properly, ensure the following:

- Each select statement returns the same number of columns
- Columns are in the same order
- Each column should be of the same type

## Syntax

![Flow chart showing the syntax of the UNION keyword](/img/docs/diagrams/union.svg)

- `UNION` will return distinct results.
- `UNION ALL` will return all results including duplicates.

## Examples

Consider two tables, listA and listB, shown below.

listA

| Description | ID  |
| ----------- | --- |
| Red Pen     | 1   |
| Blue Pen    | 2   |
| Green Pen   | 3   |

listB

| Description | ID  |
| ----------- | --- |
| Pink Pen    | 1   |
| Black Pen   | 2   |
| Green Pen   | 3   |

```questdb-sql
listA UNION listB
```

will return

| Description | ID  |
| ----------- | --- |
| Red Pen     | 1   |
| Blue Pen    | 2   |
| Green Pen   | 3   |
| Pink Pen    | 1   |
| Black Pen   | 2   |

```questdb-sql
listA UNION ALL listB
```

will return

| Description | ID  |
| ----------- | --- |
| Red Pen     | 1   |
| Blue Pen    | 2   |
| Green Pen   | 3   |
| Pink Pen    | 1   |
| Black Pen   | 2   |
| Green Pen   | 3   |
