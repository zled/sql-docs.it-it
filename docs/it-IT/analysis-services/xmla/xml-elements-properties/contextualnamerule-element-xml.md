---
title: Elemento ContextualNameRule (XML) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: eb567ef8-f412-4d34-837a-75e53b88b3ce
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bfca085e32d314ba9007ea5d1529a849ca39de68
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="contextualnamerule-element-xml"></a>Elemento ContextualNameRule (XML)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Fornisce un suggerimento sul modo migliore di costruire un nome composito per l'attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <ContextualNameRule>...</ContextualNameRule>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|-1|  
|Cardinalità|0-1: elemento facoltativo che ricorre una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[RelationshipEndVisualizationProperties](../../../analysis-services/scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Fornisce un suggerimento alle applicazioni client sulla creazione di nomi non ambigui per questo attributo.  
  
 Il valore di **ContextualNameRule** elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Value|Description|  
|-----------|-----------------|  
|*Nessuno*|Utilizzare il nome dell'attributo.|  
|*Contesto*|Utilizzare il nome della relazione in entrata.|  
|*Merge*|In base alle regole della lingua dell'applicazione, concatenare il nome della relazione in entrata e il nome dell'attributo.|  
  
  
