---
title: Oggetto Field | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Field object [ADO]
ms.assetid: 7d1c4ad5-4be3-42ab-b516-e7133ca300bc
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8b2fc3f1716f39d5c45aab95c504fef4d9e7437f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="the-field-object"></a>Oggetto Field
Ogni **campo** oggetto è in genere corrisponde a una colonna in una tabella di database. Tuttavia, un **campo** può anche rappresentare un puntatore a un altro **Recordset**, denominato capitolo. Eccezioni, ad esempio le colonne a capitoli, verranno trattate più avanti in questa Guida.  
  
 Utilizzare il **valore** proprietà di **campo** oggetti per impostare o restituire dati per il record corrente. A seconda della funzionalità espone il provider, alcuni insiemi, metodi o proprietà di un **campo** oggetto potrebbe non essere disponibile.  
  
 Con le raccolte, i metodi e proprietà di un **campo** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Restituisce il nome di un campo utilizzando il **nome** proprietà.  
  
-   Consente di visualizzare o modificare i dati nel campo utilizzando il **valore** proprietà. **Valore** è la proprietà predefinita di **campo** oggetto.  
  
-   Restituire le caratteristiche di base di un campo utilizzando il **tipo**, **precisione**, e **NumericScale** proprietà.  
  
-   Restituire la dimensione dichiarata di un campo utilizzando il **DefinedSize** proprietà.  
  
-   Restituire la dimensione effettiva dei dati in un determinato campo utilizzando il **ActualSize** proprietà.  
  
-   Determinare i tipi di funzionalità sono supportati per un determinato campo tramite il **attributi** proprietà e **proprietà** insieme.  
  
-   Modificare i valori dei campi che contengono dati long carattere o binari lungo utilizzando il **AppendChunk** e **GetChunk** metodi.  
  
 Risolvere le differenze tra i valori dei campi durante l'aggiornamento in batch utilizzando il **OriginalValue** e **UnderlyingValue** proprietà, se il provider supporta gli aggiornamenti in batch.  
  
## <a name="describing-a-field"></a>Che descrive un campo  
 Gli argomenti seguenti sono illustrano le proprietà del [campo](../../../ado/reference/ado-api/field-object.md) oggetti che rappresentano informazioni che descrivono il **campo** oggetto stesso, vale a dire i metadati relativi al campo. Queste informazioni consente di determinare le relative allo schema del **Recordset**. Queste proprietà includono **tipo**, **DefinedSize** e **ActualSize**, **nome**, e **NumericScale**e **precisione**.  
  
### <a name="discovering-the-data-type"></a>Il tipo di dati di individuazione  
 Il **tipo** proprietà indica il tipo di dati del campo. Il tipo di dati costanti enumerate sono supportate da ADO sono descritti in [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) nel *di riferimento per programmatori di ADO*.  
  
 Tipi numerici, ad esempio virgola mobile **adNumeric**, è possibile ottenere ulteriori informazioni. Il **NumericScale** proprietà indica il numero di cifre a destra del separatore decimale da utilizzare per rappresentare i valori per il **campo**. Il **precisione** proprietà specifica il numero massimo di cifre utilizzate per rappresentare i valori per il **campo**.  
  
### <a name="determining-field-size"></a>Determinazione delle dimensioni del campo  
 Utilizzare il **DefinedSize** proprietà per determinare la capacità di dati di un **campo** oggetto.  
  
 Utilizzare il **ActualSize** proprietà per restituire la lunghezza effettiva di un **campo** valore dell'oggetto. Per tutti i campi, il **ActualSize** proprietà è di sola lettura. Se ADO non è possibile determinare la lunghezza del **campo** il valore dell'oggetto, il **ActualSize** restituisce proprietà **adUnknown**.  
  
 Il **DefinedSize** e **ActualSize** proprietà hanno scopi diversi. Si consideri ad esempio un **campo** oggetto con un tipo dichiarato di **adVarChar** e **DefinedSize** valore della proprietà di 50, contenente un singolo carattere. Il **ActualSize** valore restituito della proprietà è la lunghezza in byte del carattere singolo.  
  
### <a name="determining-field-contents"></a>Determinare i contenuti del campo  
 L'identificatore della colonna dall'origine dati è rappresentato dal **nome** proprietà del **campo**. Il **valore** proprietà del **campo** oggetto restituisce o imposta il contenuto di dati effettivo del campo. Questa è la proprietà predefinita.  
  
 Per modificare i dati in un campo, impostare il **valore** proprietà è uguale a un nuovo valore del tipo corretto. Il tipo di cursore deve supportare gli aggiornamenti per modificare il contenuto di un campo. La convalida del database non viene eseguita di seguito in modalità batch, pertanto è necessario controllare gli errori quando si chiama **UpdateBatch** in questo caso. Alcuni provider supportano inoltre ADO **campo** dell'oggetto **UnderlyingValue** e **OriginalValue** proprietà per agevolare la risoluzione dei conflitti quando si tenta di eseguire gli aggiornamenti batch. Per informazioni dettagliate su come risolvere tali conflitti, vedere [modifica dei dati](../../../ado/guide/data/editing-data.md).  
  
> [!NOTE]
>  **Recordset Field** i valori non possono essere impostati quando si accoda nuove **campi** a un **Recordset**. Piuttosto, nuova **campi** può essere aggiunto a un oggetto chiuso **Recordset**. Il **Recordset** deve essere aperto e quindi solo possibile assegnare valori a questi **campi**.  
  
### <a name="getting-more-field-information"></a>Recupero di informazioni di campo  
 Gli oggetti ADO hanno due tipi di proprietà: incorporato e dinamici. A questo punto, solo le proprietà predefinite del **campo** oggetto sono state illustrate.  
  
 Le proprietà predefinite corrispondono alle proprietà implementate in ADO e immediatamente disponibili per qualsiasi nuovo oggetto tramite il `MyObject.Property` sintassi. Non vengono visualizzati come **proprietà** oggetti in un oggetto **proprietà** insieme.  
  
 Proprietà dinamiche sono definite dal provider di dati sottostante e vengono visualizzati di **proprietà** raccolta per l'oggetto ADO appropriato. Ad esempio, una proprietà specifica del provider può indicare se un **Recordset** oggetto supporta le transazioni o l'aggiornamento. Queste proprietà aggiuntive verranno visualizzate come **proprietà** gli oggetti che **Recordset** dell'oggetto **proprietà** insieme. È possibile fare riferimento a proprietà dinamiche solo tramite la raccolta utilizzando la sintassi `MyObject.Properties(0)` o `MyObject.Properties("Name")`.  
  
 È possibile eliminare il tipo di proprietà.  
  
 Dinamico **proprietà** oggetto dispone di un proprio quattro proprietà predefinite:  
  
-   Il **nome** proprietà è una stringa che identifica la proprietà.  
  
-   Il **tipo** proprietà è un numero intero che specifica il tipo di dati di proprietà.  
  
-   Il **valore** proprietà è una variabile variant contenente l'impostazione della proprietà. **Valore** è la proprietà predefinita per un **proprietà** oggetto.  
  
-   Il **attributi** proprietà è un **lungo** valore che indica le caratteristiche della proprietà specifiche del provider.  
  
 Il **proprietà** raccolta per il **campo** oggetto contiene i metadati aggiuntivi sul campo. Il contenuto di questa raccolta varia in base al provider. L'esempio di codice seguente viene illustrato il **proprietà** raccolta del campione **Recordset** introdotto all'inizio di questa sezione. Viene innanzitutto analizzato il contenuto della raccolta. Questo codice Usa il [il Provider OLE DB per SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), pertanto il **proprietà** insieme contiene informazioni rilevanti per tale provider.  
  
```  
'BeginFieldProps  
    Dim objProp As ADODB.Property  
  
    For intLoop = 0 To (objFields.Count - 1)  
        Debug.Print objFields.Item(intLoop).Name  
  
        For Each objProp In objFields(intLoop).Properties  
            Debug.Print vbTab & objProp.Name & " = " & objProp.Value  
        Next objProp  
    Next intLoop  
'EndFieldProps  
```  
  
### <a name="dealing-with-binary-data"></a>Gestione di dati binari  
 Utilizzare il [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) metodo su un **campo** oggetto per inserirvi dati long binari o character. In situazioni in cui la memoria di sistema è limitata, è possibile utilizzare il **AppendChunk** metodo per modificare i valori lunghi nelle parti anziché nella loro interezza.  
  
 Se il **adFldLong** bit il **attributi** proprietà di un **campo** oggetto è impostato su **True**, è possibile utilizzare il  **AppendChunk** metodo per tale campo.  
  
 Il primo **AppendChunk** chiamare su un **campo** oggetto scrive dati nel campo, sovrascrivendo i dati esistenti. Le successive **AppendChunk** aggiungono chiamate ai dati esistenti. Se si stanno aggiungendo dei dati a un campo e quindi impostare o leggere il valore di un altro campo del record corrente, si presume che si è terminato l'aggiunta di dati e il primo campo. Se si chiama il **AppendChunk** metodo nel primo campo, ADO interpreta la chiamata come nuovo **AppendChunk** operazione e sovrascrive i dati esistenti. L'accesso ai campi in altre **Recordset** gli oggetti che non siano cloni del primo **Recordset** oggetto non altererà **AppendChunk** operazioni.  
  
 Utilizzare il **GetChunk** metodo su un **campo** oggetto per recuperare una parte o tutti i dati long binary o character. In situazioni in cui la memoria di sistema è limitata, è possibile utilizzare il **GetChunk** metodo per modificare i valori lunghi nelle parti, anziché nella loro interezza.  
  
 I dati che un **GetChunk** chiamata viene assegnato a *variabile*. Se *dimensioni* è maggiore di dati restanti, la **GetChunk** il metodo restituisce solo i dati rimanenti senza spaziatura interna *variabile* con spazi vuoti. Se il campo è vuoto, il **GetChunk** metodo restituisce un valore null.  
  
 Ogni successivo **GetChunk** chiamata recupera i dati a partire dalla posizione precedente **GetChunk** chiamata è stata interrotta. Tuttavia, se si recuperano dati da un campo e quindi impostare o leggere il valore di un altro campo del record corrente, ADO presuppone di che avere il recupero dei dati dal primo campo. Se si chiama il **GetChunk** metodo nel primo campo, ADO interpreta la chiamata come nuovo **GetChunk** operazione e avvia la lettura dall'inizio dei dati. L'accesso ai campi in altre **Recordset** gli oggetti che non siano cloni del primo **Recordset** oggetto non altererà **GetChunk** operazioni.  
  
 Se il **adFldLong** bit il **attributi** proprietà di un **campo** oggetto è impostato su **True**, è possibile utilizzare il **GetChunk**  metodo per tale campo.  
  
 Se è presente alcun record corrente quando si utilizza il **GetChunk** o **AppendChunk** metodo su un **campo** dell'oggetto, si verifica l'errore 3021 (Nessun record corrente).  
  
 Per un esempio di utilizzo di questi metodi per modificare i dati binari, vedere il [metodo AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) e [metodo GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) negli esempi di *di ADO riferimento per programmatori*.
