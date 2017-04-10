---
title: "Editor gestione connessione file flat (pagina Avanzate) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.ffileconnection.columnproperties.f1"
helpviewer_keywords: 
  - "Editor gestione connessione file flat"
ms.assetid: 58aa3dee-4774-4e0b-a956-96d199be4c3a
caps.latest.revision: 36
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 36
---
# Editor gestione connessione file flat (pagina Avanzate)
  Usare la pagina **Avanzate** della finestra di dialogo **Editor gestione connessione file flat** per impostare le proprietà che specificano come Integration Services legge e scrive i dati nei file flat. È possibile modificare i nomi delle colonne del file flat e impostare le proprietà che includono il tipo di dati e i delimitatori per ogni colonna del file.  
  
 Per impostazione predefinita, la lunghezza delle colonne di stringhe è di 50 caratteri. È possibile ridimensionare la lunghezza di queste colonne per evitare che i dati siano troncati o che la colonna sia eccessivamente larga. È possibile aggiornare anche altri metadati per attivare la compatibilità con le colonne di destinazione. È possibile ad esempio modificare il tipo di dati di una colonna che contiene solo dati integer impostando un tipo di dati numeric, come DT_I2. È possibile apportare manualmente queste modifiche oppure fare clic sul pulsante **Suggerisci tipi** per usare la finestra di dialogo **Suggerisci tipi di colonne** per valutare i dati di esempio e apportare tali modifiche automaticamente.  
  
 Per ulteriori informazioni sull'Editor gestione connessione file flat, vedere [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
## Opzioni  
 **Nome gestione connessione**  
 Consente di specificare un nome univoco per la gestione connessione file flat nel flusso di lavoro. Il nome specificato verrà visualizzato in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **Description**  
 Consente di aggiungere una descrizione per la gestione connessione. È consigliabile includere nella descrizione informazioni sugli scopi della gestione connessione, in modo da ottenere pacchetti autodocumentati e semplificarne quindi la gestione.  
  
 **Configurare le proprietà delle singole colonne**  
 È possibile selezionare una colonna nel riquadro sinistro per visualizzarne le proprietà in quello destro. Nella tabella seguente è disponibile una descrizione delle proprietà dei tipi di dati. Alcune delle proprietà incluse nell'elenco possono essere configurate solo per alcuni formati di file flat.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**ColumnType**|Indica se la colonna è delimitata, a larghezza fissa o non allineata a destra. Questa proprietà è di sola lettura. I file non allineati a destra sono file in cui ogni colonna ha una larghezza fissa, ad eccezione dell'ultima. L'ultima colonna è delimitata dal delimitatore di riga.|  
|**OutputColumnWidth**|Consente di specificare il valore da archiviare come conteggio di byte. Nel caso dei file Unicode tale valore corrisponde al conteggio di caratteri. Nell'attività Flusso di dati questo valore viene utilizzato per impostare la larghezza della colonna di output per l'origine file flat. Nel modello a oggetti il nome di questa proprietà è MaximumWidth.|  
|**DataType**|Consente di selezionare i tipi di dati disponibili nell'apposito elenco. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).|  
|**TextQualified**|Consente di indicare se i dati di tipo testo sono racchiusi tra qualificatori di testo, ad esempio le virgolette.<br /><br /> True: i dati di tipo testo nel file flat sono qualificati. False: i dati di tipo testo nel file flat NON sono qualificati.|  
|**Nome**|Consente di specificare un nome descrittivo per la colonna. Se non si immettere alcun nome, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea automaticamente un nome nel formato Colonna 0, Colonna 1 e così via.|  
|**DataScale**|Consente di specificare la scala dei dati numerici. Per scala si intende il numero di posizioni decimali. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).|  
|**ColumnDelimiter**|Consente di selezionare i delimitatori di colonna disponibili nell'apposito elenco. Scegliere come delimitatori caratteri che non siano già presenti nel testo. Questo valore viene ignorato per le colonne a larghezza fissa.<br /><br /> **{CR}{LF}**. Le colonne sono delimitate dalla combinazione di caratteri ritorno a capo/avanzamento riga.<br /><br /> **{CR}**. Le colonne sono delimitate da un ritorno a capo.<br /><br /> **{LF}**. Le colonne sono delimitate da un avanzamento riga.<br /><br /> **Punto e virgola {;}**. Le colonne sono delimitate da un punto e virgola.<br /><br /> **Due punti {:}**. Le colonne sono delimitate da due punti.<br /><br /> **Virgola {,}**. Le colonne sono delimitate da una virgola.<br /><br /> **Tabulazione {t}**. Le colonne sono delimitate da una tabulazione.<br /><br /> **Barra verticale {&#124;}**. Le colonne sono delimitate da una barra verticale.|  
|**DataPrecision**|Consente di specificare la precisione dei dati numerici. Per precisione si intende il numero di cifre. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).|  
|**InputColumnWidth**|Consente di specificare il valore da archiviare come conteggio di byte. Nel caso dei file Unicode tale valore verrà visualizzato come conteggio di caratteri. Questo valore viene ignorato nelle colonne delimitate.<br /><br /> **Nota** Nel modello a oggetti il nome di questa proprietà è ColumnWidth.|  
  
 **Nuova**  
 Consente di aggiungere una** **nuova colonna. Per impostazione predefinita, il pulsante **Nuova** aggiunge una colonna alla fine dell'elenco. Il pulsante dispone inoltre delle opzioni seguenti, disponibili nell'elenco a discesa.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Aggiungi colonna**|Consente di aggiungere una nuova colonna alla fine dell'elenco.|  
|**Inserisci prima**|Consente di inserire una nuova colonna prima di quella selezionata.|  
|**Inserisci dopo**|Consente di inserire una nuova colonna dopo quella selezionata.|  
  
 **Elimina**  
 Consente di selezionare una colonna e quindi di** **rimuoverla.  
  
 **Suggerisci tipi**  
 La finestra di dialogo **Suggerisci tipi di colonne** consente di valutare dati di esempio nel file e ottenere suggerimenti sul tipo di dati e sulla lunghezza di ogni colonna. Per altre informazioni, vedere [Riferimento all'interfaccia utente della finestra di dialogo Suggerisci tipi di colonne](../../integration-services/connection-manager/suggest-column-types-dialog-box-ui-reference.md).  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor gestione connessione file flat &#40;pagina Generale&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md)   
 [Editor gestione connessione file flat &#40;pagina Colonne&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-columns-page.md)   
 [Editor gestione connessione file flat &#40;pagina Anteprima&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md)  
  
  