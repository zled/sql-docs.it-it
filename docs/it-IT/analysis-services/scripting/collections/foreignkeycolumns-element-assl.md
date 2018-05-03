---
title: Elemento ForeignKeyColumns (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ForeignKeyColumns Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ForeignKeyColumns
helpviewer_keywords:
- ForeignKeyColumns element
ms.assetid: 0a673c1a-73dd-4217-aa41-56b340b5e1ab
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5c9b0096331fb8834d241837a6a47ffa57344808
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="foreignkeycolumns-element-assl"></a>Elemento ForeignKeyColumns (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la raccolta di colonne che identificano il join alla tabella padre per un'origine dati relazionale.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructureColumn xsi:type="TableMiningStructureColumn">  
   ...  
   <ForeignKeyColumns>  
      <ForeignKeyColumn xsi:type="DataItem">...</ForeignKeyColumn>  
...</ForeignKeyColumns>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md) di tipo [TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|  
|Elementi figlio|[ForeignKeyColumn](../../../analysis-services/scripting/objects/foreignkeycolumn-element-assl.md) di tipo [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento MiningStructure &#40;ASSL&#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)   
 [Raccolte & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
