---
title: Elemento DTAXML (DTA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 175cfd247df19129f39d1e4ed8914da32dd57d11
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

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
  
|Attribute|Descrizione|  
|---------------|-----------------|  
|**xmlns:xsi**|Obbligatorio. Identifica lo spazio dei nomi di istanze di XML Schema. Gli attributi da questo spazio dei nomi sono utilizzati per fare riferimento allo schema utilizzato per convalidare il file XML di Ottimizzazione guidata motore di database.<br /><br /> Valore obbligatorio: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|**xmlns**|Obbligatorio. Identifica lo spazio dei nomi di Ottimizzazione guidata motore di database.<br /><br /> Se il file XML di Ottimizzazione guidata motore di database viene modificato utilizzando l'editor XML in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], questo valore è utilizzato da F1 Guida e Guida dinamica per individuare i possibili argomenti di riferimento nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Valore obbligatorio:<br /><br /> Spazio dei nomi[XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?LinkId=43100) |  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuno|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Obbligatorio una volta per ogni file DTA XML.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|Nessuno|  
|**Elementi figlio**|[Elemento DTAInput &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)<br /><br /> Elemento**DTAOutput** . Per informazioni, vedere [Database Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) (Schema XML dell'Ottimizzazione guidata motore di database).|  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sugli spazi dei nomi XML, vedere [Spazi dei nomi in un documento XML](http://go.microsoft.com/fwlink/?LinkId=7341) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.  
  
## <a name="example"></a>Esempio  
 Per esempi di elementi **DTAXML** tipici, vedere [Esempi di file di input XML &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento al File di Input XML &#40; motore di Database, ottimizzazione guidata &#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)   
 [Avvio e utilizzo di Ottimizzazione guidata motore di database](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  

