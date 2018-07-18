---
title: Proprietà personalizzate di Excel | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bdcc72b8-8950-47bd-88bf-5db6d48cc6bf
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 34fe10fcfbfde6494ff1b2a354d3958ac65e372c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235291"
---
# <a name="excel-custom-properties"></a>Proprietà personalizzate di Excel
  **Proprietà personalizzate delle origini**  
  
 L'origine Excel include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate dell'origine Excel. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Valore intero|Modalità utilizzata per accedere al database. I valori possibili sono **set di righe aperto**, **OPENROWSET da variabile**, `SQL Command`, e **comando SQL da variabile**. Il valore predefinito è **OpenRowset**.|  
|CommandTimeout|Valore intero|Numero di secondi prima del timeout del comando.  Il valore 0 indica un timeout infinito.<br /><br /> **Nota** Questa proprietà non è disponibile in **Editor origine Excel**, ma può essere impostata tramite **Editor avanzato**.|  
|OpenRowset|String|Nome dell'oggetto di database utilizzato per aprire un set di righe.|  
|OpenRowsetVariable|String|Variabile che contiene il nome dell'oggetto di database utilizzato per aprire un set di righe.|  
|ParameterMapping|String|Mapping tra i parametri nel comando SQL e le variabili.|  
|SqlCommand|String|Comando SQL da eseguire.|  
|SqlCommandVariable|String|Variabile che contiene il comando SQL da eseguire.|  
  
 L'output e le colonne di output dell'origine Excel non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Origine Excel](excel-source.md).  
  
 **Proprietà personalizzate delle destinazioni**  
  
 La destinazione Excel include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione Excel. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (enumerazione)|Valore che specifica la modalità di accesso della destinazione al relativo database di destinazione.<br /><br /> Di seguito vengono indicati i possibili valori della proprietà.<br /><br /> `OpenRowset` (0): specificare il nome di una tabella o vista.<br /><br /> `OpenRowset from Variable` (1), ovvero è fornire il nome di una variabile che contiene il nome di una tabella o vista.<br /><br /> `OpenRowset Using Fastload` (3): specificare il nome di una tabella o di una vista.<br /><br /> `OpenRowset Using Fastload from Variable` (4), ovvero è fornire il nome di una variabile che contiene il nome di una tabella o vista.<br /><br /> `SQL Command` (2): specificare un'istruzione SQL.|  
|CommandTimeout|Valore intero|Numero massimo di secondi durante i quali è possibile eseguire il comando SQL prima del timeout. Il valore **0** corrisponde a un intervallo infinito. Il valore predefinito di questa proprietà è **0**.<br /><br /> Nota: questa proprietà non è disponibile in **Editor destinazione Excel**, ma può essere impostata tramite **Editor avanzato**.|  
|FastLoadKeepIdentity|Boolean|Valore che specifica se copiare i valori Identity durante il caricamento dei dati. Questa proprietà è disponibile solo quando si utilizza una delle opzioni di caricamento rapido. Il valore predefinito di questa proprietà è **False**.|  
|FastLoadKeepNulls|Boolean|Valore che specifica se copiare i valori Null durante il caricamento dei dati. Questa proprietà è disponibile solo con una delle opzioni di caricamento rapido. Il valore predefinito di questa proprietà è **False**.|  
|FastLoadMaxInsertCommitSize|Valore intero|Valore che specifica le dimensioni del batch di cui la destinazione Excel tenta di eseguire il commit durante le operazioni di caricamento rapido. Il valore predefinito è **2147483647**. Il valore **0** indica una singola operazione di commit in seguito all'elaborazione di tutte le righe.|  
|FastLoadOptions|String|Raccolta di opzioni di caricamento rapido. Tra le opzioni di caricamento rapido sono inclusi il blocco delle tabelle e la verifica dei vincoli. È possibile specificare una, nessuna o entrambe le opzioni.<br /><br /> Nota: alcune opzioni per questa proprietà non sono disponibili in **Editor destinazione Excel**, ma possono essere impostate usando **Editor avanzato**.|  
|OpenRowset|String|Quando AccessMode è `OpenRowset`, il nome della tabella o della vista a cui accede la destinazione Excel.|  
|OpenRowsetVariable|String|Quando AccessMode è `OpenRowset from Variable`, il nome della variabile che contiene il nome della tabella o della vista a cui accede la destinazione Excel.|  
|SqlCommand|String|Quando AccessMode è `SQL Command`, l'istruzione Transact-SQL utilizzata dalla destinazione Excel per specificare le colonne di destinazione per i dati.|  
  
 L'input e le colonne di input della destinazione Excel non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione Excel](excel-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](../common-properties.md)  
  
  
