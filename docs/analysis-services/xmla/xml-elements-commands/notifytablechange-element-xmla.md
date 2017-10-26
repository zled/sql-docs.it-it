---
title: Elemento NotifyTableChange (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- NotifyTableChange Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#NotifyTableChange
- http://schemas.microsoft.com/analysisservices/2003/engine#NotifyTableChange
- microsoft.xml.analysis.notifytablechange
helpviewer_keywords:
- NotifyTableChange command
ms.assetid: b76898eb-20d3-48c8-9eb8-1fd5df638bcc
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 45e156076d7d97164fcb43674e3975daf6944e1e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="notifytablechange-element-xmla"></a>Elemento NotifyTableChange (XMLA)
  Notifica a un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] che alle tabelle in un'origine dati specificata è stata modificata.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <NotifyTableChange>  
      <Object>...</Object>  
      <TableNotifications>...</TableNotifications>  
   </NotifyTableChange>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [TableNotifications](../../../analysis-services/xmla/xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **NotifyTableChange** comando consente a un'applicazione client di notificare in modo esplicito un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza che uno o più tabelle contenute in un'origine dati sono state modificate. Per la memorizzazione nella cache attiva, questa notifica indica che gli oggetti OLAP (ROLAP) relazionali basati su quelle tabelle devono essere rivisti e aggiornati.  
  
 Questo metodo di notifica viene utilizzato meglio per oggetti ROLAP basati su viste o query denominate definite in una vista origine dati per la quale è difficile rilevare e registrare le modifiche.  
  
 Il **oggetto** elemento deve fare riferimento a un'origine dati nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database. Se il **oggetto** elemento fa riferimento a un oggetto diverso da un'origine dati, si verifica un errore.  
  
 Per altre informazioni sulla memorizzazione nella cache attiva, vedere [Memorizzazione nella cache attiva &#40;partizioni&#41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

