---
title: I record e campi specificati dal Provider | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- records-provided fields [ADO]
- provider-supplied fields [ADO]
ms.assetid: 77f95e0a-0cf2-411a-a792-593f77330fbd
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 93b97bce2562604a01c564a376bd093abb9b1b7c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="records-and-provider-supplied-fields"></a>I record e campi specificati dal Provider
Quando un [Record](../../../ado/reference/ado-api/record-object-ado.md) viene aperto, la relativa origine può essere la riga corrente di un elemento aperto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), un URL assoluto o un URL relativo in combinazione con un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto .  
  
 Se il **Record** viene aperto da un **Recordset**, **Record** oggetto [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta conterrà tutti i campi di  **Recordset**, nonché tutti i campi aggiunti dal provider sottostante.  
  
 Il provider può inserire campi aggiuntivi che fungono da caratteristiche supplementari del **Record**. Di conseguenza, un **Record** può includere campi univoci non nel **Recordset** come intero o una qualsiasi **Record** derivato da un'altra riga del **Recordset**.  
  
 Ad esempio, tutte le righe di un **Recordset** derivato da un messaggio con origine dati potrebbe disporre di colonne, ad esempio, a e il soggetto. Oggetto **Record** derivato dalla classe **Recordset** avranno gli stessi campi. Tuttavia, il **Record** può disporre anche di altri campi specifici del particolare messaggio rappresentato da tale **Record**, ad esempio allegato e Cc (copia).  
  
 Sebbene il **Record** oggetto e la riga corrente del **Recordset** gli stessi campi sono diversi perché **Record** e **Recordset**gli oggetti hanno proprietà e metodi diversi.  
  
 Un campo comune al **Record** e **Recordset** può essere modificata per uno di questi oggetti. Tuttavia, non è possibile eliminare il campo sul **Record** dell'oggetto, anche se il provider sottostante può supportare l'impostazione del campo su null.  
  
 Dopo il **Record** è aperto, è possibile aggiungere a livello di codice i campi. È anche possibile eliminare i campi che sono stati aggiunti ma non è possibile eliminare i campi dall'originale **Recordset**.  
  
 È inoltre possibile aprire il **Record** oggetto direttamente da un URL. In questo caso, aggiungere i campi di **Record** dipendono dal provider sottostante. La maggior parte dei provider aggiunge un set di campi che descrivono l'entità rappresentata dal **Record**. Se l'entità è costituita da un flusso di byte, ad esempio un file semplice, un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto può essere aperta in genere dal **Record**.  
  
## <a name="special-fields-for-document-source-providers"></a>Provider di origine di campi specifici per documento  
 Una classe speciale di provider, detti *i provider di origine del documento*, gestisce cartelle e documenti. Quando un **Record** oggetto rappresenta un documento o un **Recordset** oggetto rappresenta una cartella di documenti, il provider di origine del documento consente di popolare gli oggetti con un set univoco di campi che descrivono caratteristiche del documento invece di effettivi del documento stesso. In genere, un campo contiene un riferimento al **flusso** che rappresenta il documento.  
  
 Questi campi costituiscono una risorsa **record** o **recordset** e sono elencate per il provider specifici che li supportano in [appendice a: provider](../../../ado/guide/appendixes/appendix-a-providers.md).  
  
 Indice di due costanti di **campi** raccolta di una risorsa **Record** o **Recordset** per recuperare una coppia di campi di uso comune. Il **campo** oggetto [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà restituisce il contenuto desiderato.  
  
-   Il campo a cui si accede con il **adDefaultStream** costante contiene un flusso predefinito associato il **Record** o **Recordset** oggetto. Il provider assegna un flusso predefinito a un oggetto.  
  
-   Il campo a cui si accede con il **adRecordURL** costante contiene l'URL assoluto che identifica il documento.  
  
 Un provider di origine del documento non supporta il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme di **Record** e **campo** oggetti. Il contenuto del **proprietà** raccolta è null per tali oggetti.  
  
 Un provider di origine del documento è possibile aggiungere una proprietà specifica del provider, ad esempio **tipo di origine dati** per identificare se un provider di origine del documento. Per ulteriori informazioni su come determinare il tipo di provider, vedere la documentazione del provider.  
  
## <a name="resource-recordset-columns"></a>Colonne dei Recordset risorsa  
 Oggetto *recordset di risorsa* costituito dalle colonne seguenti.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|RESOURCE_PARSENAME|AdVarWChar|Di sola lettura. Indica l'URL della risorsa.|  
|RESOURCE_PARENTNAME|AdVarWChar|Di sola lettura. Indica l'URL assoluto del record padre.|  
|RESOURCE_ABSOLUTEPARSENAME|AdVarWChar|Di sola lettura. Indica l'URL assoluto della risorsa, che rappresenta la concatenazione di PARENTNAME e PARSENAME.|  
|CUI RESOURCE_ISHIDDEN|adBoolean|True se la risorsa è nascosto. A meno che il comando che crea in modo esplicito il set di righe seleziona le righe in cui RESOURCE_ISHIDDEN è True, verrà restituita alcuna riga.|  
|RESOURCE_ISREADONLY|adBoolean|True se la risorsa è di sola lettura. Tenta di aprire questa risorsa con DBBINDFLAG_WRITE ed esito negativo con DBBINDFLAG_WRITE. Questa proprietà può essere modificata anche quando la risorsa è stata aperta solo per la lettura.|  
|RESOURCE_CONTENTTYPE|AdVarWChar|Indica l'utilizzo probabile del documento, ad esempio, un documento legale del breve. Può corrispondere al modello di Office che è stato utilizzato per creare il documento.|  
|RESOURCE_CONTENTCLASS|AdVarWChar|Indica il tipo MIME del documento, che indica il formato, ad esempio "`text/html`".|  
|RESOURCE_CONTENTLANGUAGE|AdVarWChar|Indica la lingua in cui è archiviato il contenuto.|  
|RESOURCE_CREATIONTIME|adFileTime|Di sola lettura. Indica una struttura FILETIME che contiene l'ora di che creazione della risorsa. Il tempo è espresso nel formato Coordinated Universal Time (UTC).|  
|RESOURCE_LASTACCESSTIME|adFileTime|Di sola lettura. Indica una struttura FILETIME che contiene l'ora dell'ultimo accesso alla risorsa. L'ora è in formato UTC. I membri FILETIME sono pari a zero se il provider non supporta questo membro temporale.|  
|RESOURCE_LASTWRITETIME|adFileTime|Di sola lettura. Indica una struttura FILETIME che contiene l'ora dell'ultima scrittura della risorsa. L'ora è in formato UTC. I membri FILETIME sono pari a zero se il provider non supporta questo membro temporale.|  
|RESOURCE_STREAMSIZE|asUnsignedBigInt|Di sola lettura. Indica le dimensioni della risorsa predefinita, in byte del flusso.|  
|RESOURCE_ISCOLLECTION|adBoolean|Di sola lettura. True se la risorsa è una raccolta, ad esempio una directory. False se la risorsa è un file semplice.|  
|RESOURCE_ISSTRUCTUREDDOCUMENT|adBoolean|True se la risorsa è un documento strutturato. False se la risorsa non è un documento strutturato. Potrebbe trattarsi di una raccolta o un file semplice.|  
|DEFAULT_DOCUMENT|AdVarWChar|Di sola lettura. Indica che la risorsa contiene un URL per il documento semplice predefinito di una cartella o un documento strutturato. Utilizzato quando viene richiesto il flusso predefinito da una risorsa. Questa proprietà è vuota per un file semplice.|  
|CHAPTERED_CHILDREN|AdChapter|Di sola lettura. Facoltativa. Indica il capitolo del set di righe che contiene gli elementi figlio della risorsa. (Il *il Provider OLE DB per Internet Publishing* non usare questa colonna.)|  
|RESOURCE_DISPLAYNAME|AdVarWChar|Di sola lettura. Indica il nome visualizzato della risorsa.|  
|RESOURCE_ISROOT|adBoolean|Di sola lettura. True se la risorsa è la radice di una raccolta o di un documento strutturato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Appendice a: provider](../../../ado/guide/appendixes/appendix-a-providers.md)

