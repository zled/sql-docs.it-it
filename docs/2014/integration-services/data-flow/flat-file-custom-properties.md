---
title: Proprietà personalizzate del file flat | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6f5f69e807734412ab5ed6706e699fa73c9dcaa5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209601"
---
# <a name="flat-file-custom-properties"></a>Proprietà personalizzate del file flat
  **Proprietà personalizzate delle origini**  
  
 L'origine file flat include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate dell'origine file flat. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|FileNameColumnName|String|Nome di una colonna di output contenente il nome file. Se non si specifica alcun nome, non verrà generata alcuna colonna contenente il nome file.<br /><br /> Nota: questa proprietà non è disponibile in **Editor origine file flat**, ma può essere impostata tramite **Editor avanzato**.|  
|RetainNulls|Boolean|Valore che specifica se i valori Null dal file di origine devono essere mantenuti come tali durante l'elaborazione dei dati tramite il motore della pipeline di trasformazione dati. Il valore predefinito di questa proprietà è `False`.|  
  
 L'output dell'origine file flat non include proprietà personalizzate.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate delle colonne di output dell'origine file flat. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|FastParse|Boolean|Valore che indica se la colonna utilizza le routine di analisi più veloci ma indipendenti dalle impostazioni locali disponibili in DTS oppure le routine di analisi standard dipendenti dalle impostazioni locali. Per altre informazioni, vedere [Analisi veloce](../fast-parse.md) e [Analisi standard](../standard-parse.md). Il valore predefinito di questa proprietà è `False`.<br /><br /> Nota: questa proprietà non è disponibile in **Editor origine file flat**, ma può essere impostata tramite **Editor avanzato**.|  
  
 Per altre informazioni, vedere [Origine file flat](flat-file-source.md).  
  
 **Proprietà personalizzate delle destinazioni**  
  
 La destinazione file flat include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione file flat. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|Intestazione|String|Blocco di testo inserito nel file prima di iniziare a scrivere i dati.<br /><br /> È possibile specificare il valore di questa proprietà tramite un'espressione di proprietà.|  
|Overwrite|Boolean|Valore che specifica se sovrascrivere o aggiungere dati a un file di destinazione esistente con lo stesso nome. Il valore predefinito di questa proprietà è `True`.|  
  
 L'input e le colonne di input della destinazione file flat non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione file flat](flat-file-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](../common-properties.md)  
  
  
