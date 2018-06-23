---
title: Introduzione ai DiffGram in SQLXML 4.0 | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- annotations [SQLXML]
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: 1902d67f-baf3-46e6-a36c-b24b5ba6f8ea
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 05f1374292eb3f1024c12519417ae872ffeb3734
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054294"
---
# <a name="introduction-to-diffgrams-in-sqlxml-40"></a>Introduzione ai DiffGram in SQLXML 4.0
  In questo argomento viene fornita una breve introduzione ai DiffGram.  
  
## <a name="diffgram-format"></a>Formato DiffGram  
 Il formato DiffGram generale è il seguente:  
  
```  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
   <DataInstance>  
      ...  
   </DataInstance>  
   [<diffgr:before>  
        ...  
   </diffgr:before>]  
  
   [<diffgr:errors>  
        ...  
   </diffgr:errors>]  
</diffgr:diffgram>  
```  
  
 Il formato DiffGram è costituito dai blocchi seguenti:  
  
 **\<DataInstance >**  
 Il nome di questo elemento **DataInstance**, viene utilizzato a scopo esplicativo nella presente documentazione. Se, ad esempio, il DiffGram è stato generato da un set di dati in .NET Framework, il valore di **nome** proprietà del set di dati non verrebbe utilizzata come nome di questo elemento. Questo blocco contiene tutti i dati rilevanti dopo la modifica, inclusi eventualmente i dati che non sono stati modificati. La logica di elaborazione DiffGram ignora gli elementi in questo blocco per il quale il **diffgr: HasChanges** attributo non è specificato.  
  
 **\<diffgr:before>**  
 Questo blocco facoltativo contiene le istanze dei record originali (elementi) che devono essere aggiornate o eliminate. Tutte le tabelle di database modificate (aggiornate o eliminate) dal DiffGram devono essere visualizzate come elementi di livello principale nel  **\<prima di >** blocco.  
  
 **\<diffgr: Errors >**  
 Questo blocco facoltativo viene ignorato dalla logica di elaborazione DiffGram.  
  
## <a name="diffgram-annotations"></a>Annotazioni DiffGram  
 Queste annotazioni sono definite nello spazio dei nomi DiffGram **"urn: schemas-microsoft-com: xml-diffgram-01"**:  
  
 **id**  
 Questo attributo viene utilizzato per abbinare gli elementi nel  **\<prima di >** e il  **\<DataInstance >** blocchi.  
  
 **hasChanges**  
 Per un'istruzione insert o un'operazione di aggiornamento, il DiffGram necessario specificare questo attributo con il valore **inserito** oppure **modificato**. Se questo attributo non è presente, l'elemento corrispondente nel  **\<DataInstance >** viene ignorato per l'elaborazione della logica e non vengono eseguiti aggiornamenti. Per esempi reali, vedere [esempi di DiffGram &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).  
  
 **parentID**  
 Questo attributo viene utilizzato per specificare relazioni padre-figlio tra gli elementi nel DiffGram. Questo attributo viene visualizzato solo nel \<prima > blocco. e viene utilizzato da SQLXML durante l'applicazione di aggiornamenti. La relazione padre-figlio viene utilizzata per determinare l'ordine in cui gli elementi vengono elaborati nel DiffGram.  
  
## <a name="understanding-the-diffgram-processing-logic"></a>Informazioni sulla logica di elaborazione DiffGram  
 La logica di elaborazione DiffGram utilizza determinate regole per stabilire se un'operazione è di inserimento, aggiornamento o eliminazione. Tali regole sono descritte nella tabella seguente:  
  
|Operazione|Description|  
|---------------|-----------------|  
|Insert|Un DiffGram indica un'operazione di inserimento quando un elemento viene visualizzato nel  **\<DataInstance >** blocco ma non nel corrispondente  **\<prima >** blocco e il **diffgr: HasChanges** sia specificato l'attributo (**diffgr: HasChanges = inserito**) sull'elemento. In questo caso, il DiffGram inserisce l'istanza del record specificata nel  **\<DataInstance >** blocco nel database.<br /><br /> Se il **diffgr: HasChanges** attributo non viene specificato, l'elemento viene ignorato dalla logica di elaborazione e viene eseguito alcun inserimento. Per esempi reali, vedere [esempi di DiffGram &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).|  
|Update|Il DiffGram indica un'operazione di aggiornamento quando c'è un elemento nel \<prima di > per cui è disponibile un elemento corrispondente in blocco il  **\<DataInstance >** blocco (ovvero, entrambi gli elementi hanno un **diffgr: ID** attributo con valore stesso) e il **diffgr: HasChanges** attributo viene specificato con il valore **modificato** sull'elemento nel  **\<DataInstance >** blocco.<br /><br /> Se il **diffgr: HasChanges** attributo non viene specificato sull'elemento nel  **\<DataInstance >** blocco, viene restituito un errore dalla logica di elaborazione. Per esempi reali, vedere [esempi di DiffGram &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).<br /><br /> Se **diffgr: parentId** è specificato nella  **\<prima >** blocco, la relazione padre-figlio degli elementi specificati da **parentID** vengono utilizzati in determinare l'ordine in cui vengono aggiornati i record.|  
|DELETE|Un DiffGram indica un'operazione di eliminazione quando un elemento viene visualizzato nel  **\<prima di >** blocco ma non nel corrispondente  **\<DataInstance >** blocco. In questo caso, il DiffGram Elimina l'istanza del record specificata nel  **\<prima di >** blocco dal database. Per esempi reali, vedere [esempi di DiffGram &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).<br /><br /> Se **diffgr: parentId** è specificato nella  **\<prima >** blocco, la relazione padre-figlio degli elementi specificati da **parentID** vengono utilizzati in determinare l'ordine in cui vengono eliminati i record.|  
  
> [!NOTE]  
>  Non è possibile passare parametri ai DiffGram.  
  
  