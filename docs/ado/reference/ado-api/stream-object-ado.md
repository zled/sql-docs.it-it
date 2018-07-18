---
title: Flusso di oggetto (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Stream
helpviewer_keywords:
- Stream object [ADO]
ms.assetid: 0514531f-009d-4519-abc3-d727014a39f1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 591bf956cea85979f72bb513cb08c48f86883aa3
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282600"
---
# <a name="stream-object-ado"></a>Oggetto di flusso (ADO)
Rappresenta un flusso di dati binari o di testo.  
  
 Nelle gerarchie di struttura ad albero, ad esempio un file system o un sistema di posta elettronica, un [Record](../../../ado/reference/ado-api/record-object-ado.md) può essere un flusso di binario predefinito di bit associati che contiene il contenuto del file o posta elettronica. Oggetto **flusso** oggetto può essere utilizzato per modificare i campi o record contenenti tali flussi di dati. Oggetto **flusso** oggetto può essere ottenuto nei modi seguenti:  
  
-   Da un URL che punta a un oggetto contenente dati binari o di testo (in genere un file). Questo oggetto può essere un semplice documento, un **Record** oggetto che rappresenta un documento strutturato o in una cartella.  
  
-   Aprendo il valore predefinito **flusso** oggetto associato a un **Record** oggetto. È possibile ottenere il flusso predefinito associato a un **Record** oggetto quando il **Record** viene aperto, per eliminare un round trip per aprire il flusso.  
  
-   Creando un **flusso** oggetto. Questi **flusso** gli oggetti possono essere utilizzati per archiviare i dati ai fini dell'applicazione. A differenza di un **flusso** associata a un URL o il valore predefinito **flusso** di un **Record**, un'istanza **flusso** Nessuna associazione con un origine sottostante per impostazione predefinita.  
  
 Con i metodi e proprietà di un **flusso** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Aprire un **flusso** dell'oggetto da un **Record** o l'URL con il [aprire](../../../ado/reference/ado-api/open-method-ado-stream.md) metodo.  
  
-   Chiudere un **flusso** con il [Chiudi](../../../ado/reference/ado-api/close-method-ado.md) metodo.  
  
-   Input di byte o testo in un **flusso** con il [scrivere](../../../ado/reference/ado-api/write-method.md) e [WriteText](../../../ado/reference/ado-api/writetext-method.md) metodi.  
  
-   Byte da leggere la **flusso** con il [lettura](../../../ado/reference/ado-api/read-method.md) e [ReadText](../../../ado/reference/ado-api/readtext-method.md) metodi.  
  
-   Scrivere eventuali **flusso** del buffer di dati in ADO all'oggetto sottostante con il [scaricamento](../../../ado/reference/ado-api/flush-method-ado.md) metodo.  
  
-   Copiare il contenuto di un **flusso** a un altro **flusso** con il [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) metodo.  
  
-   Controllare la modalità di lettura delle righe dal file di origine con il [SkipLine](../../../ado/reference/ado-api/skipline-method.md)(metodo) e [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) proprietà.  
  
-   Determinare l'estremità della posizione del flusso con il [fine del flusso](../../../ado/reference/ado-api/eos-property.md)proprietà e [SetEOS](../../../ado/reference/ado-api/seteos-method.md) metodo.  
  
-   Salvare e ripristinare i dati in file con il [SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)e [LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md) metodi.  
  
-   Specificare il set di caratteri utilizzato per archiviare il **flusso** con il [Charset](../../../ado/reference/ado-api/charset-property-ado.md) proprietà.  
  
-   Interrompere asincrono **flusso** operazione con il [Annulla](../../../ado/reference/ado-api/cancel-method-ado.md) metodo.  
  
-   Determinare il numero di byte in un **flusso** con il [dimensioni](../../../ado/reference/ado-api/size-property-ado-stream.md) proprietà.  
  
-   Controllare la posizione corrente all'interno di un **flusso** con il [posizione](../../../ado/reference/ado-api/position-property-ado.md) proprietà.  
  
-   Determinare il tipo di dati in un **flusso** con il [tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) proprietà.  
  
-   Determinare lo stato corrente del **flusso** (chiuso, aperto, o l'esecuzione) con il [stato](../../../ado/reference/ado-api/state-property-ado.md) proprietà.  
  
-   Specificare la modalità di accesso per il **flusso** con il [modalità](../../../ado/reference/ado-api/mode-property-ado.md) proprietà.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Il **flusso** oggetto è sicuro per lo script.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Le proprietà dell'oggetto flusso, metodi ed eventi](../../../ado/reference/ado-api/stream-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Record e flussi](../../../ado/guide/data/records-and-streams.md)
