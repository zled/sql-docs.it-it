---
title: Elemento NotifyTableChange (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6b379fde8b0561af0af41cabcef1b91adf459a26
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="notifytablechange-element-xmla"></a>Elemento NotifyTableChange (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
 [Comandi & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
