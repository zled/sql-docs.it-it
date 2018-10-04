---
title: Elemento NotifyTableChange (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NotifyTableChange Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#NotifyTableChange
- http://schemas.microsoft.com/analysisservices/2003/engine#NotifyTableChange
- microsoft.xml.analysis.notifytablechange
helpviewer_keywords:
- NotifyTableChange command
ms.assetid: b76898eb-20d3-48c8-9eb8-1fd5df638bcc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 25d060b73f7fb5999d4eb04faaa209eb7713f9d8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224433"
---
# <a name="notifytablechange-element-xmla"></a>Elemento NotifyTableChange (XMLA)
  Notifica a un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] una modifica apportata alle tabelle in un'origine dati specificata.  
  
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Oggetto](../xml-elements-properties/object-element-xmla.md), [TableNotifications](../xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il comando `NotifyTableChange` consente a un'applicazione client di notificare in modo esplicito un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] che una o più tabelle contenute in un'origine dati sono state modificate. Per la memorizzazione nella cache attiva, questa notifica indica che gli oggetti OLAP (ROLAP) relazionali basati su quelle tabelle devono essere rivisti e aggiornati.  
  
 Questo metodo di notifica viene utilizzato meglio per oggetti ROLAP basati su viste o query denominate definite in una vista origine dati per la quale è difficile rilevare e registrare le modifiche.  
  
 L'elemento `Object` deve riferirsi a un'origine dati nel database [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Se l'elemento `Object` fa riferimento a un oggetto diverso da un’origine dati, si verifica un errore.  
  
 Per altre informazioni sulla memorizzazione nella cache attiva, vedere [Memorizzazione nella cache attiva &#40;partizioni&#41;](../../multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="see-also"></a>Vedere anche  
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
