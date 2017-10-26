---
title: "Proprietà personalizzate del File flat | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 097c9a07d738bb1b192095ac91448487fdfa0eb1
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="flat-file-custom-properties"></a>Proprietà personalizzate del file flat
  **Proprietà personalizzate delle origini**  
  
 L'origine file flat include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate dell'origine file flat. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|FileNameColumnName|String|Nome di una colonna di output contenente il nome file. Se non si specifica alcun nome, non verrà generata alcuna colonna contenente il nome file.<br /><br /> Nota: questa proprietà non è disponibile in **Editor origine file flat**, ma può essere impostata tramite **Editor avanzato**.|  
|RetainNulls|Boolean|Valore che specifica se i valori Null dal file di origine devono essere mantenuti come tali durante l'elaborazione dei dati tramite il motore della pipeline di trasformazione dati. Il valore predefinito di questa proprietà è **False**.|  
  
 L'output dell'origine file flat non include proprietà personalizzate.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate delle colonne di output dell'origine file flat. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|FastParse|Boolean|Valore che indica se la colonna utilizza le routine di analisi più veloci ma indipendenti dalle impostazioni locali disponibili in DTS oppure le routine di analisi standard dipendenti dalle impostazioni locali. Per altre informazioni, vedere [Analisi veloce](http://msdn.microsoft.com/library/6688707d-3c5b-404e-aa2f-e13092ac8d95) e [Analisi standard](http://msdn.microsoft.com/library/dfe835b1-ea52-4e18-a23a-5188c5b6f013). Il valore predefinito di questa proprietà è **False**.<br /><br /> Nota: questa proprietà non è disponibile in **Editor origine file flat**, ma può essere impostata tramite **Editor avanzato**.|  
  
 Per altre informazioni, vedere [Origine file flat](../../integration-services/data-flow/flat-file-source.md).  
  
 **Proprietà personalizzate delle destinazioni**  
  
 La destinazione file flat include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione file flat. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|Intestazione|String|Blocco di testo inserito nel file prima di iniziare a scrivere i dati.<br /><br /> È possibile specificare il valore di questa proprietà tramite un'espressione di proprietà.|  
|Overwrite|Boolean|Valore che specifica se sovrascrivere o aggiungere dati a un file di destinazione esistente con lo stesso nome. Il valore predefinito di questa proprietà è **True**.|  
  
 L'input e le colonne di input della destinazione file flat non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione file flat](../../integration-services/data-flow/flat-file-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  

