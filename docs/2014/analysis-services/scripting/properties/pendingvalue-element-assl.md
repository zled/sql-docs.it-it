---
title: Elemento PendingValue (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- PendingValue Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PendingValue
helpviewer_keywords:
- PendingValue element
ms.assetid: 386b2ec6-3d83-42d2-b83a-83e375fbdcbd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c0f78f1916f9d6b4cd266848d5b5c5943fb17cc9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117419"
---
# <a name="pendingvalue-element-assl"></a>Elemento PendingValue (ASSL)
  Contiene la sola lettura in sospeso al valore dell'oggetto associato [ServerProperty](../objects/serverproperty-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ServerProperty>  
   ...  
   <PendingValue>...</PendingValue>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Any simpleType|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ServerProperty](../objects/serverproperty-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Questo elemento contiene il valore della `ServerProperty` che verrà utilizzata alla successiva esecuzione l'istanza corrente di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene avviato. Questo valore viene in genere recuperato da qualunque posizione in cui è archiviato il valore della proprietà del server, ovvero un file di inizializzazione, il Registro di sistema di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows o un altro meccanismo di archiviazione.  
  
 L'elemento che corrisponde al padre di `PendingValue` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ServerProperties &#40;ASSL&#41;](../collections/serverproperties-element-assl.md)   
 [Elemento server &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
