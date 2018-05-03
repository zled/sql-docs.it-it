---
title: Elemento alias (ASSL) | Documenti Microsoft
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
- Alias Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Alias
helpviewer_keywords:
- Alias element
ms.assetid: 674fdb06-e33c-4f35-bd6a-d9bbb13ececa
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 83b37bf4be8f9b59dba886db11862b895c34fd72
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="alias-element-assl"></a>Elemento Alias (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un alias per un [Account](../../../analysis-services/scripting/objects/account-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Aliases>  
      <Alias>...</Alias>  
</Aliases>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Alias](../../../analysis-services/scripting/collections/aliases-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore della **Alias** elemento viene usato come nome alternativo per l'account definito per il **Account** elemento padre che consente di identificare la combinazione della funzione di aggregazione e tipo di account utente interfaccia.  
  
 L'elemento che corrisponde all'elemento padre di **alias** insieme nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
