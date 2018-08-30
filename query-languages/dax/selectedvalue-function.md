---
title: "SELECTEDVALUE Function | Microsoft Docs"
ms.prod: dax
ms.date: 5/22/2018
ms.reviewer: owend
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
---
# SELECTEDVALUE Function
Returns the value when the context for columnName has been filtered down to one distinct value only. Otherwise returns alternateResult.  
  
## Syntax  
  
```  
SELECTEDVALUE(<columnName>[, <alternateResult>])  
```  
  
#### Parameters  
  
|Term|Definition|  
|----------|--------------|  
| columnName |The name of an existing column, using standard DAX syntax. It cannot be an expression. |  
| alternateResult |(Optional) The value returned when the context for columnName has been filtered down to zero or more than one distinct value. When not provided, the default value is BLANK().| 
 
## Return Value  
The value when the context for columnName has been filtered down to one distinct value only. Else, alternateResult. 
  
  
## Remarks  
An equivalent expression for `SELECTEDVALUE(<columnName>, <alternateResult>)` is `IF(HASONEVALUE(<columnName>), VALUES(<columnName>), <alternateResult>)`. 
  
## Example  
  
The following DAX query:

```
DEFINE MEASURE DimProduct[Selected Color] = SELECTEDVALUE(DimProduct[Color], "No Single Selection")
EVALUATE SUMMARIZECOLUMNS(ROLLUPADDISSUBTOTAL(DimProduct[Color], "Is Total"), "Selected Color", [Selected Color])
ORDER BY [Is Total] ASC, [Color] ASC
```

Returns the following:

DimProduct[Color]  |[Is Total]  |[Selected Color] 
---------|---------|---------|
Black     |  FALSE       |   Black      |
Blue     |   FALSE      |    Blue     |
Grey     |  FALSE       |   Grey      |
Multi     |   FALSE      |   Multi     | 
NA     |   FALSE      |      NA   |
Red     |  FALSE       |   Red     | 
Silver     |  FALSE       |  Silver   |      
Silver/Black     | FALSE        |   Silver/Black |     
White     |   FALSE      |  White       |
Yellow    | FALSE        |  Yellow       |
| | TRUE | No Single Selection| 

