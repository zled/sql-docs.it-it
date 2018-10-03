---
title: Elemento Source (Synchronize) (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Source Element (Synchronize)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Source
- http://schemas.microsoft.com/analysisservices/2003/engine#Source
- microsoft.xml.analysis.source
helpviewer_keywords:
- Source element
ms.assetid: 0a857f91-771f-4c5e-8bf7-4bf17442d4df
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 900a52341995a058ea98a2ee44e344971f3dd4dd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090073"
---
# <a name="source-element-synchronize-xmla"></a>Elemento Source (Synchronize) (XMLA)
  Rappresenta un database di origine da cui sincronizzare un database di destinazione durante una [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Synchronize>  
   <Source>  
      <Object>...</Object>  
      <ConnectionString>...</ConnectionString>  
   </Source>  
</Synchronize>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Sincronizza](../xml-elements-commands/synchronize-element-xmla.md)|  
|Elementi figlio|[ConnectionString](connectionstring-element-xmla.md), [oggetto](object-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il `Synchronize` comando Usa il `Source` elemento per stabilire una connessione a e identificare un database in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] con cui sincronizzare il database di destinazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
