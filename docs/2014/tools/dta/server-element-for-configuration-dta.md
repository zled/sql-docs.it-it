---
title: Elemento server per Configuration (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10a8fa9eed7f89d9706ab3388eccc881b165ef74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48206911"
---
# <a name="server-element-for-configuration-dta"></a>Elemento Server per Configuration (DTA)
  Contiene le informazioni di identificazione per il server in cui si desidera Database Ottimizzazione guidata motore di valutazione della configurazione ipotetica (specificato da di `Configuration` elemento).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Obbligatorio una sola volta per ogni `Configuration` elemento.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento di configurazione &#40;DTA&#41;](configuration-element-dta.md)|  
|**Elementi figlio**|[Nome di elemento per il Server &#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Elemento database per la configurazione &#40;DTA&#41;](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Note  
 È possibile specificare una sola `Server` (elemento) per il `Configuration` elemento. Questo elemento appartiene al Name **ServerTypecomplexType** nell' [XML Schema dell'ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100). Non confondere questa `Server` con quello che è l'elemento figlio dell'elemento di `DTAInput` elemento. Per altre informazioni, vedere [Elemento Server &#40;DTA&#41;](server-element-dta.md).  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
