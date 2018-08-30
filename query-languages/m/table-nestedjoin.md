---
title: "Table.NestedJoin | Microsoft Docs"
ms.date: 4/16/2018
ms.prod: power-query
ms.reviewer: owend
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
---
# Table.NestedJoin
<code>Table.NestedJoin(<b>table1</b> as table, <b>key1</b> as any, <b>table2</b> as any, <b>key2</b> as any, <b>newColumnName</b> as text, optional <b>joinKind</b> as nullable number, optional <b>keyEqualityComparers</b> as nullable list) as table</code>

## About
<p>Joins the rows of <code>table1</code> with the rows of <code>table2</code> based on the equality of the values of the key columns selected by <code>key1</code> (for <code>table1</code>) and <code>key2</code> (for <code>table2</code>). The results are entered into the column named <code>newColumnName</code>.</p> <p>The optional <code>joinKind</code> specifies the kind of join to perform. By default, a left outer join is performed if a <code>joinKind</code> is not specified.</p> <p>An optional set of <code>keyEqualityComparers</code> may be included to specify how to compare the key columns.</p> 