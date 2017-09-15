---
title: Servizio cursore Microsoft per OLE DB (componente del servizio ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- providers [ADO], cursor service for OLE DB
- cursor service for OLE DB [ADO]
ms.assetid: 420d0989-7cfb-4c66-a7b5-f4199d13165d
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d7a1f8568b633417196c6c9dda3e8a3615146603
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-cursor-service-for-ole-db-overview"></a>Servizio cursore per una panoramica OLE DB Microsoft
Il servizio di cursore per OLE DB Microsoft integra le funzioni di supporto cursore dei provider di dati. Di conseguenza, l'utente utilizza funzionalità relativamente uniforme di tutti i provider di dati.

 Il servizio cursore rende disponibili le proprietà dinamiche e migliora il comportamento di alcuni metodi. Ad esempio, il [Ottimizza](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) proprietà dinamica consente la creazione di indici temporanei per rendere alcune operazioni, ad esempio il [trovare](../../../ado/reference/ado-api/find-method-ado.md) metodo.

 Il servizio cursore consente il supporto per l'aggiornamento in batch in tutti i casi. Inoltre, simula più in grado di supportare tipi di cursore, ad esempio i cursori dinamici, quando un provider di dati possa fornire solo i cursori meno in grado di supportare, ad esempio i cursori statici.

## <a name="keyword"></a>Parola chiave
 Per richiamare questo componente del servizio, impostare il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) o [connessione](../../../ado/reference/ado-api/connection-object-ado.md) dell'oggetto [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà **adUseClient**.

```
connection.CursorLocation=adUseClient
recordset.CursorLocation=adUseClient
```

## <a name="dynamic-properties"></a>Proprietà dinamiche
 Quando viene richiamato il servizio di cursore per OLE DB, le proprietà dinamiche seguenti vengono aggiunti per il **Recordset** dell'oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme. L'elenco completo dei **connessione** e **Recordset** le proprietà dell'oggetto dinamico è elencato nella [ADO Dynamic Property Index](../../../ado/reference/ado-api/ado-dynamic-property-index.md). I nomi di proprietà OLE DB associati, laddove appropriato, sono racchiusi tra parentesi dopo il nome della proprietà ADO.

 Modifiche di alcune proprietà dinamiche non sono visibili all'origine dati sottostante dopo che il servizio di cursore è stato richiamato. Ad esempio, impostando il *timeout del comando* proprietà in un **Recordset** non sarà visibile al provider di dati sottostante.

```

Recordset1.CursorLocation = adUseClient     'invokes cursor service
Recordset1.Open "authors", _
    "Provider=SQLOLEDB;Data Source=DBServer;User Id=MyUserID;" & _
    "Password=MyPassword;Initial Catalog=pubs;",,adCmdTable
Recordset1.Properties.Item("Command Time out") = 50
' 'Command Time out' property on DBServer is still default (30).

```

 Se l'applicazione richiede che il servizio di cursore, ma è necessario impostare le proprietà dinamiche per il provider sottostante, è possibile impostare le proprietà prima di richiamare il servizio di cursore. Le impostazioni delle proprietà di oggetto comando vengono sempre passate al provider di dati sottostante, indipendentemente dalla posizione del cursore. Pertanto, è possibile utilizzare anche un oggetto comando per impostare le proprietà in qualsiasi momento.

> [!NOTE]
>  La proprietà dinamica DBPROP_SERVERDATAONINSERT non è supportata dal servizio di cursore, anche se è supportato dal provider di dati sottostante.

|Nome proprietà|Description|
|-------------------|-----------------|
|Ricalcolo automatico (DBPROP_ADC_AUTORECALC)|Per i recordset creati con il Data shaping, questo valore indica la frequenza con cui vengono calcolate le colonne calcolate e di aggregazione. Il valore predefinito (valore = 1) consiste nel ricalcolare ogni volta che il Data Shaping determina che i valori sono stati modificati. Se il valore è 0, le colonne calcolate o di aggregazione vengono calcolate solo quando viene inizialmente creata la gerarchia.|
|Dimensioni del batch (DBPROP_ADC_BATCHSIZE)|Indica il numero di istruzioni update che possono essere raggruppate prima dell'invio all'archivio dati. Le altre istruzioni in un batch, archiviare meno round trip ai dati.|
|Memorizzare nella cache le righe figlio (DBPROP_ADC_CACHECHILDROWS)|Per i recordset creati con il Data shaping, questo valore indica se il recordset figlio viene archiviato in una cache per un uso successivo.|
|Versione del motore del cursore (DBPROP_ADC_CEVER)|Indica la versione del servizio cursore in uso.|
|Gestire lo stato di modifica (DBPROP_ADC_MAINTAINCHANGESTATUS)|Indica il testo del comando utilizzato per la risincronizzazione un una o più righe in un join tra più tabelle.|
|[Ottimizzazione](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Indica se è necessario creare un indice. Se impostato su **True**, autorizza la creazione di indici per migliorare l'esecuzione di determinate operazioni temporanea.|
|[Modificare la forma di nome](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Indica il nome del **Recordset**. Può essere a cui fa riferimento all'interno dell'oggetto, o successive, i comandi di shaping dei dati.|
|[Risincronizzazione di comando](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Indica una stringa di comando personalizzato che viene utilizzata il [Resync](../../../ado/reference/ado-api/resync-method.md) metodo quando il [tabella univoca](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) è attiva.|
|[Catalogo univoca](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Indica il nome del database contenente la tabella a cui fa riferimento il **tabella univoca** proprietà.|
|[Schema univoco](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Indica il nome del proprietario della tabella a cui fa riferimento il **tabella univoca** proprietà.|
|[Tabella univoca](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Indica il nome di una tabella in un **Recordset** creato da più tabelle che possono essere modificate per gli inserimenti, aggiornamenti o eliminazioni.|
|Criteri di aggiornamento (DBPROP_ADC_UPDATECRITERIA)|Indica che i campi di **dove** clausola vengono utilizzati per gestire i conflitti che si verificano durante un aggiornamento.|
|[Aggiornare risincronizzazione](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) (DBPROP_ADC_UPDATERESYNC)|Indica se il **Resync** metodo viene richiamato in modo implicito dopo la [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) metodo (e il relativo comportamento), quando il **tabella univoca** è attiva.|

 È anche possibile impostare o recuperare una proprietà dinamica specificandone il nome dell'indice per il **proprietà** insieme. Ad esempio, ottenere e visualizzare il valore corrente del [Ottimizza](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) proprietà dinamiche, quindi impostare un nuovo valore, come indicato di seguito:

```
Debug.Print rs.Properties("Optimize")
rs.Properties("Optimize") = True
```

## <a name="built-in-property-behavior"></a>Comportamento delle proprietà predefinite
 Il servizio di cursore per OLE DB influisce anche sul comportamento di alcune proprietà predefinite.

|Nome proprietà|Description|
|-------------------|-----------------|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|Integra i tipi di cursori che sono disponibili per un **Recordset**.|
|[Tipo di blocco](../../../ado/reference/ado-api/locktype-property-ado.md)|Integra i tipi di blocchi disponibili per un **Recordset**. Consente gli aggiornamenti in blocco.|
|[Sort](../../../ado/reference/ado-api/sort-property.md)|Specifica i nomi dei campi di uno o più che il **Recordset** viene ordinato se e in ogni campo viene ordinato in ordine crescente o decrescente.|

## <a name="method-behavior"></a>Comportamento del metodo
 Consente di attivare il servizio di cursore per OLE DB o influisce sul comportamento del [campo](../../../ado/reference/ado-api/field-object.md) dell'oggetto [Append](../../../ado/reference/ado-api/append-method-ado.md) metodo; e **Recordset** dell'oggetto [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), e [salvare](../../../ado/reference/ado-api/save-method.md) metodi.

