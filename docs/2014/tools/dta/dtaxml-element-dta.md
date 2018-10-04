---
title: Elemento DTAXML (DTA) | Microsoft Docs
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
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d567c422299809f04be97c8db298aadecc22dde8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48192221"
---
# <a name="dtaxml-element-dta"></a>Elemento DTAXML (DTA)
  L'elemento radice di un file di input o di output XML di Ottimizzazione guidata motore di database, **DTAXML** , contiene tutti gli elementi che descrivono l'input e l'output di ottimizzazione generati da Ottimizzazione guidata motore di database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a>Attributi elemento  
  
|attribute|Description|  
|---------------|-----------------|  
|`xmlns:xsi`|Obbligatorio. Identifica lo spazio dei nomi di istanze di XML Schema. Gli attributi da questo spazio dei nomi sono utilizzati per fare riferimento allo schema utilizzato per convalidare il file XML di Ottimizzazione guidata motore di database.<br /><br /> Valore obbligatorio: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|`xmlns`|Obbligatorio. Identifica lo spazio dei nomi di Ottimizzazione guidata motore di database.<br /><br /> Se il file XML di Ottimizzazione guidata motore di database viene modificato utilizzando l'editor XML in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], questo valore è utilizzato da F1 Guida e Guida dinamica per individuare i possibili argomenti di riferimento nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Valore obbligatorio:<br /><br /> Spazio dei nomi[XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?LinkId=43100) |  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Obbligatorio una volta per ogni file DTA XML.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|None|  
|**Elementi figlio**|[Elemento DTAInput &#40;DTA&#41;](dtainput-element-dta.md)<br /><br /> `DTAOutput` Elemento (vedere [Engine Tuning Advisor XML schema di Database](http://schemas.microsoft.com/sqlserver/) per informazioni)|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sugli spazi dei nomi XML, vedere [Spazi dei nomi in un documento XML](http://go.microsoft.com/fwlink/?LinkId=7341) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.  
  
## <a name="example"></a>Esempio  
 Per esempi di elementi **DTAXML** tipici, vedere [Esempi di file di input XML &#40;DTA&#41;](xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento a un File di Input XML &#40;Ottimizzazione guidata motore di Database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)   
 [Avviare e usare Ottimizzazione guidata motore di database](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
