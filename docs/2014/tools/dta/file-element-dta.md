---
title: Elemento File (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- File element
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 856ca7cb2ef9c0ab70eeb410db3ef6748b159bcf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157858"
---
# <a name="file-element-dta"></a>Elemento File (DTA)
  Specifica il file del carico di lavoro. Un carico di lavoro è un set di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] eseguite sui database che si desidera ottimizzare. I file del carico di lavoro possono essere costituiti da script [!INCLUDE[tsql](../../includes/tsql-md.md)] (sql) o file di traccia (trc). Per altre informazioni, vedere [Avvio e utilizzo di Ottimizzazione guidata motore di database](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAInput>  
  <Server>...</Server>  
  <Workload>  
    <File>...</File>  
  </Workload>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Utilizzare il tipo di dati `string` per specificare il percorso della directory del file del carico di lavoro. Esempio:<br /><br /> `<File>C:\Tuning\tun.sql</File>`<br /><br /> Il limite della lunghezza è imposto dal server.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Obbligatorio una sola volta se non viene specificato un altro tipo di carico di lavoro. È necessario specificare un elemento figlio **EventString**, **File**o **Database** per l'elemento padre **Workload** , ma è possibile utilizzare un solo tipo. Se ad esempio si specifica un carico di lavoro con l'elemento **File** , non sarà possibile specificare anche un carico di lavoro con l'elemento **Database** nello stesso file di input XML.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Workload &#40;DTA&#41;](workload-element-dta.md)|  
|**Elementi figlio**|Nessuna.|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML semplice &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  