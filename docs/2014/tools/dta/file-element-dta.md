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
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- File element
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0cf6b51bf7f6d4f90a8a575326beb457e42e5d99
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159762"
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
  
  
