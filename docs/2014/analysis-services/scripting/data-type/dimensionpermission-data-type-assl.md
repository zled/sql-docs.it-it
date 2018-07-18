---
title: Tipo di dati DimensionPermission (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DimensionPermission Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DimensionPermission data type
ms.assetid: 066405ff-903f-467a-b0d5-e58653952c52
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 740479b334195b36ac7f8d04446575917da04d02
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178838"
---
# <a name="dimensionpermission-data-type-assl"></a>Tipo di dati DimensionPermission (ASSL)
  Definisce un tipo di dati derivato che rappresenta le autorizzazioni assegnate a una dimensione del database.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionPermission>  
   <!-- The following elements extend Permission -->  
   <AttributePermissions>...</AttributePermissions>  
   <AllowedRowsExpression>...</AllowedRowsExpression>  
</DimensionPermission>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Autorizzazione](permission-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[AttributePermissions](../collections/attributepermissions-element-assl.md), [AllowedRowsExpression](../collections/attributepermissions-element-assl.md)|  
|Elementi derivati|[Elemento DimensionPermission](../objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 Questo elemento dispone delle convalide seguenti in DeploymentMode, valore 2 (modalità server tabulare).  
  
-   *AttributePermission* attributo deve essere vuoto o si verifica un errore.  
  
 Questo elemento dispone delle convalide seguenti in DeploymentMode, valore 0 (OLAP).  
  
-   *AllowedRowsExpression* attributo deve essere vuoto o si verifica un errore.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DimensionPermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
