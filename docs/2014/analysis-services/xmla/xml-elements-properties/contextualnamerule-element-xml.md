---
title: Elemento ContextualNameRule (XML) | Documenti Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: eb567ef8-f412-4d34-837a-75e53b88b3ce
caps.latest.revision: 7
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 6b3d4e8f8023814fb0080b5ba7d9196aad81afee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157229"
---
# <a name="contextualnamerule-element-xml"></a>Elemento ContextualNameRule (XML)
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|-1|  
|Cardinalità|0-1: elemento facoltativo che ricorre una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Fornisce un suggerimento alle applicazioni client sulla creazione di nomi non ambigui per questo attributo.  
  
 Il valore dell'elemento `ContextualNameRule` è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Nessuno*|Utilizzare il nome dell'attributo.|  
|*Contesto*|Utilizzare il nome della relazione in entrata.|  
|*Merge*|In base alle regole della lingua dell'applicazione, concatenare il nome della relazione in entrata e il nome dell'attributo.|  
  
  