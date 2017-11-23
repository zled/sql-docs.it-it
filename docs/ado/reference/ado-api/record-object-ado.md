---
title: Registrare l'oggetto (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Record
helpviewer_keywords: Record object [ADO]
ms.assetid: db83ed2c-a8e3-460c-8682-64667e4d5d01
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0efb504844ac58e7889cdb768821efe95f52e0b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="record-object-ado"></a>Oggetto di record (ADO)
Rappresenta una riga da un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) o il provider di dati o un oggetto restituito dal provider di dati semistrutturati e non strutturati, ad esempio un file o directory.  
  
## <a name="remarks"></a>Osservazioni  
 Oggetto **Record** oggetto rappresenta una riga di dati e presenta alcune analogie con una sola riga concettuale **Recordset**. A seconda delle funzionalità del provider, **Record** oggetti possono essere restituiti direttamente dal proprio provider anziché a una riga **Recordset**, ad esempio quando una query SQL che seleziona solo una riga eseguito. O, **Record** oggetto può essere ottenuto direttamente da un **Recordset** oggetto. O, **Record** può essere restituito direttamente da un provider di dati semistrutturati, ad esempio il provider OLE DB di Microsoft Exchange.  
  
 È possibile visualizzare i campi associati il **Record** dall'oggetto di [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta il **Record** oggetto. ADO consente le colonne con valori di oggetto inclusi **Recordset**, **SafeArray**e i valori scalari di **campi** insieme di **Record** oggetti.  
  
 Se il **Record** oggetto rappresenta una riga in un **Recordset**, è possibile tornare a questo originale **Recordset** con il [origine](../../../ado/reference/ado-api/source-property-ado-record.md) proprietà.  
  
 Il **Record** oggetto può anche essere utilizzato dai provider di dati semistrutturati, ad esempio il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md), per gli spazi dei nomi con struttura ad albero del modello. Ogni nodo nell'albero è un **Record** oggetto con colonne associate. Le colonne possono rappresentare gli attributi di tale nodo e altre informazioni rilevanti. Il **Record** oggetto può rappresentare un nodo foglia sia un nodo non foglia della struttura ad albero. I nodi non foglia sono altri nodi come il relativo contenuto, ma i nodi foglia non dispone di tale contenuto. I nodi foglia contengono in genere flussi binari di dati e i nodi non foglia possono anche essere un flusso binario predefinito associato. Proprietà di **Record** oggetto identificano il tipo di nodo.  
  
 Il **Record** oggetto rappresenta inoltre un modo alternativo per spostarsi in ordine gerarchico organizzati i dati. Oggetto **Record** oggetto può essere creata per rappresentare la radice di un sottoalbero specifico in una struttura ad albero di grandi dimensioni e nuovi **Record** gli oggetti possono essere aperti per rappresentare i nodi figlio.  
  
 Una risorsa (ad esempio, un file o directory) può essere identificata in modo univoco un URL assoluto. A [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto viene creato e impostato su in modo implicito il **Record** oggetto quando il **Record** viene aperto tramite un URL assoluto. Oggetto **connessione** oggetto può essere impostato in modo esplicito sul **Record** oggetto tramite il [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) proprietà. I file e directory in cui è possibile accedere tramite il **connessione** oggetto definiscono il *contesto* in cui **Record** possono verificarsi operazioni.  
  
 Metodi di modifica e l'esplorazione dei dati sul **Record** oggetto accetta anche un URL relativo, che consente di individuare una risorsa tramite un URL assoluto o **connessione** contesto dell'oggetto come un punto di partenza.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Oggetto **connessione** è associato a ogni oggetto **Record** oggetto. Pertanto, **Record** operazioni oggetto possono essere parte di una transazione richiamando **connessione** metodi dell'oggetto.  
  
 Il **Record** oggetto non supporta gli eventi ADO e pertanto non risponde alle notifiche.  
  
 Con i metodi e proprietà di un **Record** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Impostare o restituire l'oggetto associato **connessione** dell'oggetto con il [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) proprietà.  
  
-   Indicare le autorizzazioni di accesso con il [modalità](../../../ado/reference/ado-api/mode-property-ado.md) proprietà.  
  
-   Restituisce l'URL della directory, se presente, che contiene la risorsa rappresentata dal **Record** con il [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md) proprietà.  
  
-   Indicare l'URL assoluto, il relativo URL, o **Recordset** da cui il **Record** derivato con il [origine](../../../ado/reference/ado-api/source-property-ado-record.md) proprietà.  
  
-   Indicare lo stato corrente del **Record** con il [stato](../../../ado/reference/ado-api/state-property-ado.md) proprietà.  
  
-   Indicare il tipo di **Record** : *semplice*, *raccolta*, o *documenti strutturati* , con la [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)proprietà.  
  
-   Arrestare l'esecuzione di un'operazione asincrona con il [Annulla](../../../ado/reference/ado-api/cancel-method-ado.md) metodo.  
  
-   Annullare l'associazione di **Record** da un'origine dati con il [Chiudi](../../../ado/reference/ado-api/close-method-ado.md) metodo.  
  
-   Copiare il file o directory rappresentata da un **Record** in un'altra posizione con il [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) metodo.  
  
-   Eliminare il file o directory e sottodirectory, rappresentato da un **Record** con il [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md) metodo.  
  
-   Aprire un **Recordset** che contiene le righe che rappresentano le sottodirectory e i file dell'entità rappresentata dal **Record** con il [GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md) metodo.  
  
-   Spostare o rinominare il file o directory e sottodirectory, rappresentato da un **Record** in un'altra posizione con il [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) metodo.  
  
-   Associare il **Record** con i dati esistenti di origine o creare un nuovo file o directory con il [aprire](../../../ado/reference/ado-api/open-method-ado-record.md) metodo.  
  
 Il **Record** oggetto è sicuro per lo script.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Record](../../../ado/reference/ado-api/record-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta di campi (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [I record e flussi](../../../ado/guide/data/records-and-streams.md)   
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
