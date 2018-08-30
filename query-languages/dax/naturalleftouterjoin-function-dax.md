---
title: "NATURALLEFTOUTERJOIN Function (DAX) | Microsoft Docs"
ms.prod: dax
ms.date: 5/22/2018
ms.reviewer: owend
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
---
# NATURALLEFTOUTERJOIN Function (DAX)
  
Performs an inner join of a table with another table. The tables are joined on common columns (by name) in the two tables. If the two tables have no common column names, an error is returned.  
  
## Syntax  
  
```  
NATURALLEFTOUTERJOIN(<leftJoinTable>, <rightJoinTable>)  
```  
  
#### Parameters  
  
|Term|Definition|  
|--------|--------------|  
|**leftJoinTable**|A table expression defining the table on the left side of the join.|  
|**rightJoinTable**|A table expression defining the table on the right side of the join.|  
  
## Return Value  
A table which includes only rows from rightJoinTable for which the values in the common columns specified are also present in leftJoinTable. The table returned will have the common columns from the left table and the other columns from both the tables.  
  
## Remarks  
There is no sort order guarantee for the results.  
  
Columns being joined on must have the same data type in both tables.  
  
Only columns from the same source table (have the same lineage) are joined on. For example, Products[ProductID], WebSales[ProductdID], StoreSales[ProductdID] with many-to-one relationships between WebSales and StoreSales and the Products table based on the ProductID column, WebSales and StoreSales tables are joined on [ProductID].  
  
Strict comparison semantics are used during join. There is no type coercion; for example, 1 does not equal 1.0.  
  