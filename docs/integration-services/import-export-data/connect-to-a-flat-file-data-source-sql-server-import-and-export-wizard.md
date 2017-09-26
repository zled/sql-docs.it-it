---
title: Connettersi a un'origine dati File Flat (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7e7067b-f5a5-482f-b97e-9d82fe8e9f76
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b765b02717c0eef59fda5dfa12cb64a1b9197587
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard"></a>Connettersi a un'origine dati File Flat (SQL Server importazione / esportazione guidata)
In questo argomento viene illustrato come connettersi a un **file flat** di origine dati (file di testo) dal **scegliere un'origine dati** o **scegliere una destinazione** pagina di esportazione e importazione di SQL Server Procedura guidata. Per i file flat, queste due pagine della procedura guidata presentano diversi set di opzioni, pertanto in questo argomento descrive l'origine file flat e la destinazione separatamente.

## <a name="connect-to-a-flat-file-source"></a>Connettersi a un'origine file flat
 
 Esistono quattro pagine di opzioni per le origini dati di file flat. Che vengono sottoposti a numerose pagine! Non si dispone di dedicare molto tempo, in ogni pagina. Ecco le attività necessarie per prendere in considerazione.
 
Pagina|Consiglio  |Tipo  
----|---------|---------
**Generale**|Assicurarsi di aggiornare le opzioni di **formato** sezione.|Consigliato    
**Colonne**|Assicurarsi di controllare i delimitatori di colonna e riga (per un file delimitato) o contrassegnare le colonne (per un file a larghezza fissa).|Consigliato
**Avanzate**|Facoltativamente, selezionare i tipi di dati e altre proprietà assegnate per impostazione predefinita per le colonne.|Facoltativo
**Anteprima**|Facoltativamente, visualizzare in anteprima un campione di dati, utilizzando le impostazioni specificate.|Facoltativo

## <a name="general-page-source"></a>Pagina Generale (origine)
 Nella pagina **Generale**, selezionare il file, quindi verificare le impostazioni nella sezione **Formato**.
 
 ![Connessione file flat generale](../../integration-services/import-export-data/media/flat-file-connection-general.png)  

### <a name="options-to-specify-general-page"></a>Le opzioni per specificare (**generale** pagina)

 **Nome file**  
 Immettere il percorso e il nome del file flat.  
  
 **Sfoglia**  
 Individuare il file flat.  
  
 **Impostazioni locali**  
 Specificare le impostazioni locali per fornire informazioni specifiche della lingua per l'ordinamento e per i formati di data e ora.  
  
 **Unicode**  
 Specificare se il file viene utilizzato Unicode. Se si utilizza Unicode, è possibile specificare una tabella codici.  
  
 **Tabella codici**  
 Consente di specificare la tabella codici per il testo non Unicode.  
  
 **Formato**  
 Consente di indicare se il file utilizza delimitata, a larghezza fissa o formattazione destra incompleta.  
  
|Valore|Description|  
|-----------|-----------------|  
|Delimitato|Le colonne sono separate dai delimitatori. Specificare il delimitatore sul **colonne** pagina.|  
|A larghezza fissa|Le colonne hanno una larghezza fissa.|  
|Non allineato a destra|I file non allineati a destra sono file in cui ogni colonna ha una larghezza fissa ad eccezione dell'ultima, per la quale viene utilizzato il delimitatore di riga.|  
  
 **Qualificatore di testo**  
 Specificare il qualificatore di testo, se presente, utilizzato dal file. Ad esempio, è possibile specificare che i campi di testo siano racchiusi tra virgolette. (Questa proprietà si applica solo ai file delimitati) 
  
> [!NOTE]
> Dopo aver selezionato un qualificatore di testo, è possibile selezionare di nuovo il **Nessuno** opzione. Digitare **Nessuno** per deselezionare il qualificatore di testo.  
  
 **Delimitatore riga di intestazione**  
 Consente di selezionare il delimitatore per la riga di intestazione nell'elenco dei delimitatori disponibili oppure di immettere il testo per il delimitatore.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|La riga di intestazione è delimitata dalla combinazione di caratteri ritorno a capo/avanzamento riga.|  
|**{CR}**|La riga di intestazione è delimitata da un carattere di ritorno a capo.|  
|**{LF}**|La riga di intestazione è delimitata da un carattere di avanzamento riga.|  
|**Punto e virgola {;}**|La riga di intestazione è delimitata da un carattere punto e virgola.|  
|**Due punti {:}**|La riga di intestazione è delimitata da un carattere due punti.|  
|**Virgola {,}**|La riga di intestazione è delimitata da una virgola.|  
|**Tabulazione {t}**|La riga di intestazione è delimitata da un carattere di tabulazione.|  
|**Barra verticale {&#124;}**|La riga di intestazione è delimitata da una barra verticale.|  
  
 **Righe di intestazione da ignorare**  
 Specificare il numero di righe da ignorare nella parte superiore del file, se presente.  
  
 **Nomi di colonne nella prima riga di dati**  
 Specificare se la prima riga (dopo eventuali righe ignorate) contiene i nomi di colonna.

## <a name="columns-page---format--delimited-source"></a>Pagina colonne - formato = delimitato (origine)
 Nella pagina **Colonne** verificare l'elenco di colonne e i delimitatori che la procedura guidata ha identificato. La schermata seguente mostra la pagina dopo aver selezionato **delimitato** come formato del file flat.
 
![File flat delimitato, pagina colonne](../../integration-services/import-export-data/media/flat-file-delimited-columns-page.jpg)

### <a name="options-to-specify-columns-page---format--delimited"></a>Le opzioni per specificare (**colonne** pagina - formato = delimitato)

 **Delimitatore di riga**  
 Consente di selezionare il delimitatore di riga desiderato nell'elenco dei delimitatori disponibili oppure di immettere il testo per il delimitatore.  
  
|Valore|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Le righe sono delimitate dalla combinazione di caratteri ritorno a capo/avanzamento riga.|  
|**{CR}**|Le righe sono delimitate da un ritorno a capo.|  
|**{LF}**|Le righe sono delimitate da un avanzamento riga.|  
|**Punto e virgola {;}**|Le righe sono delimitate da un punto e virgola.|  
|**Due punti {:}**|Le righe sono delimitate da un carattere due punti.|  
|**Virgola {,}**|Le righe sono delimitate da una virgola.|  
|**Tabulazione {t}**|Le righe sono delimitate da un carattere di tabulazione.|  
|**Barra verticale {&#124;}**|Le righe sono delimitate da una barra verticale.|  
  
 **Delimitatore di colonna**  
 Consente di selezionare il delimitatore di colonna desiderato nell'elenco dei delimitatori disponibili oppure di immettere il testo per il delimitatore.  
  
|Valore|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Le colonne sono delimitate dalla combinazione di caratteri ritorno a capo/avanzamento riga.|  
|**{CR}**|Le colonne sono delimitate da un ritorno a capo.|  
|**{LF}**|Le colonne sono delimitate da un avanzamento riga.|  
|**Punto e virgola {;}**|Le colonne sono delimitate da un punto e virgola.|  
|**Due punti {:}**|Le colonne sono delimitate da due punti.|  
|**Virgola {,}**|Le colonne sono delimitate da una virgola.|  
|**Tabulazione {t}**|Le colonne sono delimitate da una tabulazione.|  
|**Barra verticale {&#124;}**|Le colonne sono delimitate da una barra verticale.|  
  
 **Anteprima righe**  
 Consente di visualizzare dati di esempio del file flat, suddivisi in righe e colonne in base alle opzioni selezionate.  
 
 **Aggiorna**  
 Se si fa clic su **Aggiorna**è possibile visualizzare gli effetti delle modifiche ai delimitatori da ignorare. Questo pulsante viene visualizzato solo dopo la modifica di altre opzioni della connessione.  
  
 **Reimposta colonne**  
 Ripristinare le colonne originali.  

## <a name="columns-page---format--fixed-width-source"></a>Pagina colonne - formato = a larghezza fissa (origine)
Nella pagina **Colonne** verificare l'elenco di colonne e i delimitatori che la procedura guidata ha identificato. La schermata seguente mostra la pagina dopo aver selezionato **a larghezza fissa** come formato del file flat.
  
![File flat, larghezza, pagina colonne fissato](../../integration-services/import-export-data/media/flat-file-fixed-width-columns-page.jpg)

### <a name="options-to-specify-columns-page---format--fixed-width"></a>Le opzioni per specificare (**colonne** pagina - formato = a larghezza fissa)

 **Carattere**  
 Consente di selezionare il tipo di carattere per la visualizzazione in anteprima dei dati.  
  
 **Colonne dati di origine**  
 Per modificare la larghezza della riga, trascinare l'indicatore di riga rosso verticale. Per modificare la larghezza delle colonne, fare clic sul righello nella parte superiore della finestra di anteprima.  
  
 **Larghezza riga**  
 Consente di specificare la larghezza della riga prima dell'aggiunta dei delimitatori per le singole colonne. In alternativa, trascinare la linea rossa verticale nella finestra di anteprima per contrassegnare la fine della riga. Il valore relativo alla larghezza della riga viene aggiornato automaticamente.  
  
 **Reimposta colonne**  
 Ripristinare le colonne originali.  
  
## <a name="columns-page---format--ragged-right-source"></a>Pagina colonne - formato = non allineato a destra (origine)
Nella pagina **Colonne** verificare l'elenco di colonne e i delimitatori che la procedura guidata ha identificato. La schermata seguente mostra la pagina dopo aver selezionato **non allineato a destra** come formato del file flat.

> [!NOTE]
> I file non allineati a destra sono file in cui ogni colonna ha una larghezza fissa ad eccezione dell'ultima, per la quale viene utilizzato il delimitatore di riga.  
 
![File flat, non allineato a destra, la pagina colonne](../../integration-services/import-export-data/media/flat-file-ragged-right-columns-page.jpg)

### <a name="options-to-specify-columns-page---format--ragged-right"></a>Le opzioni per specificare (**colonne** pagina - formato = non allineato a destra)
   
 **Carattere**  
 Consente di selezionare il tipo di carattere per la visualizzazione in anteprima dei dati.  
  
 **Colonne dati di origine**  
 Per modificare la larghezza della riga, trascinare l'indicatore di riga rosso verticale. Per modificare la larghezza delle colonne, fare clic sul righello nella parte superiore della finestra di anteprima.  
  
 **Delimitatore di riga**  
 Consente di selezionare il delimitatore di riga desiderato nell'elenco dei delimitatori disponibili oppure di immettere il testo per il delimitatore.  
  
|Valore|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Le righe sono delimitate dalla combinazione di caratteri ritorno a capo/avanzamento riga.|  
|**{CR}**|Le righe sono delimitate da un ritorno a capo.|  
|**{LF}**|Le righe sono delimitate da un avanzamento riga.|  
|**Punto e virgola {;}**|Le righe sono delimitate da un punto e virgola.|  
|**Due punti {:}**|Le righe sono delimitate da un carattere due punti.|  
|**Virgola {,}**|Le righe sono delimitate da una virgola.|  
|**Tabulazione {t}**|Le righe sono delimitate da un carattere di tabulazione.|  
|**Barra verticale {&#124;}**|Le righe sono delimitate da una barra verticale.|  
  
 **Reimposta colonne**  
 Ripristinare le colonne originali.  

## <a name="advanced-page-source"></a>Pagina avanzate (origine)
La pagina **Avanzate** mostra informazioni dettagliate su ogni colonna nell'origine dati, inclusi il tipo di dati e le dimensioni. L'immagine seguente mostra il **avanzate** pagina per la prima colonna in un file flat delimitato da virgole.

![Formato file flat delimitato, pagina avanzate](../../integration-services/import-export-data/media/flat-file-delimited-advanced-page.jpg)

Nella schermata, si noti che il **id** colonna che contiene numeri, inizialmente presenta un tipo di dati stringa.

### <a name="options-to-specify-advanced-page"></a>Le opzioni per specificare (**avanzate** pagina)

 **Configurare le proprietà delle singole colonne**  
 È possibile selezionare una colonna nel riquadro sinistro per visualizzarne le proprietà in quello destro. Vedere la tabella seguente per una descrizione delle proprietà di colonna. Alcune delle proprietà elencate sono configurabili solo per alcuni formati di file flat e per le colonne di determinati tipi di dati.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Nome**|Consente di specificare un nome descrittivo per la colonna. Se non si immettere alcun nome, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea automaticamente un nome nel formato Colonna 0, Colonna 1 e così via.|
|**ColumnDelimiter**|Consente di selezionare i delimitatori di colonna disponibili nell'apposito elenco. Scegliere come delimitatori caratteri che non siano già presenti nel testo. Questo valore viene ignorato per le colonne a larghezza fissa.<br /><br /> **{CR}{LF}**. Le colonne sono delimitate dalla combinazione di caratteri ritorno a capo/avanzamento riga.<br /><br /> **{CR}**. Le colonne sono delimitate da un ritorno a capo.<br /><br /> **{LF}**. Le colonne sono delimitate da un avanzamento riga.<br /><br /> **Punto e virgola {;}**. Le colonne sono delimitate da un punto e virgola.<br /><br /> **Due punti {:}**. Le colonne sono delimitate da due punti.<br /><br /> **Virgola {,}**. Le colonne sono delimitate da una virgola.<br /><br /> **Tabulazione {t}**. Le colonne sono delimitate da una tabulazione.<br /><br /> **Barra verticale {&#124;}**. Le colonne sono delimitate da una barra verticale.|
|**ColumnType**|Indica se la colonna è delimitata, a larghezza fissa o non allineata a destra. Questa proprietà è di sola lettura. I file non allineati a destra sono file in cui ogni colonna ha una larghezza fissa, ad eccezione dell'ultima. L'ultima colonna è delimitata dal delimitatore di riga.|  
|**InputColumnWidth**|Consente di specificare il valore da archiviare come conteggio di byte. Nel caso dei file Unicode tale valore verrà visualizzato come conteggio di caratteri. Questo valore viene ignorato nelle colonne delimitate.<br /><br /> **Nota** : nel modello a oggetti il nome di questa proprietà è ColumnWidth.|
|**DataPrecision**|Consente di specificare la precisione dei dati numerici. Per precisione si intende il numero di cifre.|
|**DataScale**|Consente di specificare la scala dei dati numerici. Per scala si intende il numero di posizioni decimali.|
|**DataType**|Consente di selezionare i tipi di dati disponibili nell'apposito elenco.<br/>Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).|
|**OutputColumnWidth**|Consente di specificare il valore da archiviare come conteggio di byte. Nel caso dei file Unicode tale valore corrisponde al conteggio di caratteri. Nell'attività Flusso di dati questo valore viene utilizzato per impostare la larghezza della colonna di output per l'origine file flat. Nel modello a oggetti il nome di questa proprietà è MaximumWidth.|  
|**TextQualified**|Consente di indicare se i dati di tipo testo sono racchiusi tra qualificatori di testo, ad esempio le virgolette.<br /><br /> True: i dati di tipo testo nel file flat sono qualificati. False: i dati di tipo testo nel file flat NON sono qualificati.|  
  
**Nuovi**  
 Consente di aggiungere una **nuova**colonna. Per impostazione predefinita, il pulsante **Nuova** aggiunge una colonna alla fine dell'elenco. Il pulsante dispone inoltre delle opzioni seguenti, disponibili nell'elenco a discesa.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Aggiungi colonna**|Consente di aggiungere una nuova colonna alla fine dell'elenco.|  
|**Inserisci prima**|Consente di inserire una nuova colonna prima di quella selezionata.|  
|**Inserisci dopo**|Consente di inserire una nuova colonna dopo quella selezionata.|  
  
 **Elimina**  
 Consente di selezionare una colonna e quindi di **rimuoverla**.  
  
 **Suggerisci tipi**  
 La finestra di dialogo **Suggerisci tipi di colonne** consente di valutare dati di esempio nel file e ottenere suggerimenti sul tipo di dati e sulla lunghezza di ogni colonna.  
 
Fare clic su **Suggerisci tipi** per visualizzare la finestra di dialogo **Suggerisci tipi di colonne**. 

![Connessione file flat suggerisci](../../integration-services/import-export-data/media/flat-file-connection-suggest.png)

Dopo aver scelto di opzioni di **Suggerisci tipi di colonne** la finestra di dialogo e fare clic su **OK**, la procedura guidata può modificare i tipi di dati di alcune colonne.

La schermata seguente mostra che, dopo aver fatto clic **Suggerisci tipi**, la procedura guidata ha riconosciuto che il **id** colonna nell'origine dati è in realtà un numero e non una stringa di testo ed è stato modificato il tipo di dati la colonna da una stringa in un intero.

![Connessione file flat avanzate dopo](../../integration-services/import-export-data/media/flat-file-connection-advanced-after.png)

Per altre informazioni, vedere [suggerire colonna tipi di finestra di dialogo casella riferimento all'interfaccia utente](../../integration-services/connection-manager/suggest-column-types-dialog-box-ui-reference.md).

## <a name="preview-page-source"></a>Pagina di anteprima (origine)

Nella pagina **Anteprima** verificare che l'elenco di colonne e i dati di esempio siano quelli desiderati.

![File flat, pagina di anteprima](../../integration-services/import-export-data/media/flat-file-preview-page.jpg)

### <a name="options-to-specify-preview-page"></a>Le opzioni per specificare (**anteprima** pagina)

 **Righe di dati da ignorare**  
 Consente di specificare il numero di righe che devono essere ignorate all'inizio del file flat.  
  
 **Anteprima righe**  
 Consente di visualizzare i dati di esempio del file flat suddivisi in colonne e righe, a seconda delle opzioni selezionate.
 
 **Aggiorna**  
 Facendo clic su **Aggiorna**, è possibile visualizzare l'effetto della modifica del numero di righe da ignorare. Questo pulsante viene visualizzato solo dopo la modifica di altre opzioni della connessione.  
 
Per altre informazioni sulla pagina **Anteprima**, vedere la pagina di riferimento di Integration Services seguente: [Editor gestione connessione file flat &#40;pagina Anteprima&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md).

## <a name="connect-to-a-flat-file-destination"></a>Connettersi a una destinazione file flat
Per una destinazione file flat, è disponibile solo una singola pagina di opzioni, come illustrato nella schermata seguente. Sfoglia per selezionare il file, quindi verificare le impostazioni di **formato** sezione.

![Connettersi alla destinazione file flat](../../integration-services/import-export-data/media/connect-to-flat-file-destination.jpg)

### <a name="options-to-specify-choose-a-destination-page"></a>Le opzioni per specificare (**scegliere una destinazione** pagina)

 **Nome file**  
 Immettere il percorso e il nome del file flat.  
  
 **Sfoglia**  
 Individuare il file flat.  
  
 **Impostazioni locali**  
 Specificare le impostazioni locali per fornire informazioni specifiche della lingua per l'ordinamento e per i formati di data e ora.  
  
 **Unicode**  
 Specificare se il file viene utilizzato Unicode. Se si utilizza Unicode, è possibile specificare una tabella codici.  
  
 **Tabella codici**  
 Consente di specificare la tabella codici per il testo non Unicode.  
  
 **Formato**  
 Consente di indicare se il file utilizza delimitata, a larghezza fissa o formattazione destra incompleta.  
  
|Valore|Description|  
|-----------|-----------------|  
|Delimitato|Le colonne sono separate dai delimitatori. Specificare il delimitatore sul **colonne** pagina.|  
|A larghezza fissa|Le colonne hanno una larghezza fissa.|  
|Non allineato a destra|I file non allineati a destra sono file in cui ogni colonna ha una larghezza fissa ad eccezione dell'ultima, per la quale viene utilizzato il delimitatore di riga.|  
  
 **Qualificatore di testo**  
 Specificare il qualificatore di testo, se presente, utilizzato dal file. Ad esempio, è possibile specificare che i campi di testo siano racchiusi tra virgolette. (Questa proprietà si applica solo ai file delimitati) 
  
> [!NOTE] 
> Dopo aver selezionato un qualificatore di testo, è possibile selezionare di nuovo il **Nessuno** opzione. Digitare **Nessuno** per deselezionare il qualificatore di testo.  

## <a name="see-also"></a>Vedere anche
[Scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


