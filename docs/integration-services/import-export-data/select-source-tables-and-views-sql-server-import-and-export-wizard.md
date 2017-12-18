---
title: Selezione tabelle e viste di origine (Importazione/Esportazione guidata SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
caps.latest.revision: "96"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 407e1b75ca60bb8a36040883c472dce8e059188e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a>Selezione tabelle e viste di origine (Importazione/Esportazione guidata SQL Server)
  Dopo aver specificato che si vuole copiare un'intera tabella o dopo aver specificato una query, l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] visualizza **Seleziona tabelle e viste di origine**. In questa pagina è possibile selezionare le tabelle e le viste esistenti da copiare. Viene poi eseguito il mapping delle tabelle di origine in tabelle di destinazione nuove o esistenti. Facoltativamente, è anche possibile esaminare il mapping di singole colonne e visualizzare in anteprima i dati di esempio.

> [!TIP]
> Se è necessario copiare più database SQL Server o più oggetti di database SQL Server diversi da tabelle e viste, usare Copia guidata database anziché Importazione/Esportazione guidata. Per altre informazioni, vedere [Utilizzo di Copia guidata database](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="screen-shot---if-youre-going-to-copy-tables"></a>Screenshot: se si copiano tabelle  
 Lo screenshot seguente illustra un esempio della pagina **Selezione tabelle e viste di origine** della procedura guidata dopo che è stata selezionata l'opzione **Copia i dati da una o più tabelle o viste** nella pagina **Impostazione copia tabella o query**. L'elenco visualizza tutte le tabelle e le viste disponibili dall'origine dati.
 
In questo esempio, l'elenco **Origine** contiene tutte le tabelle nel database di esempio AdventureWorks. La riga selezionata illustra che l'utente vuole copiare la tabella **Sales.Customer** dall'origine nella nuova tabella **Sales.CustomerNew** di destinazione. 
   
 ![Pagina Selezione tabelle dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/media/select-tables1.png "Pagina Selezione tabelle dell'Importazione/Esportazione guidata")
  
## <a name="screen-shot---if-you-provided-a-query"></a>Screenshot: se si specifica una query  
 Lo screenshot seguente illustra un esempio della pagina **Selezione tabelle e viste di origine** della procedura guidata dopo che è stata selezionata l'opzione **Scrivi una query per specificare i dati da trasferire** nella pagina **Impostazione copia tabella o query**. L'elenco **Origine** contiene un'unica riga, in cui l'elemento denominato `[Query]` rappresenta la query specificata nella pagina **Impostazione query di origine**.
 
In questo esempio, l'utente vuole copiare i risultati della query dall'origine dati nella tabella **Sales.CustomerNew** di destinazione.  
    
 ![Pagina Selezione tabelle dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/media/select-tables2.png "Pagina Selezione tabelle dell'Importazione/Esportazione guidata")  

## <a name="select-source-and-destination-tables"></a>Selezionare le tabelle di origine e di destinazione 
**Origine**  
Mediante le caselle di controllo, selezionare dall'elenco di tabelle e viste disponibili quelle da copiare nella destinazione. Per impostazione predefinita, i dati dell'origine dati vengono copiati senza modifiche. Se si crea una nuova tabella di destinazione, viene copiato senza modifiche anche lo schema per la nuova tabella, in altre parole l'elenco delle colonne e le relative proprietà, dall'origine dati.

Se è stata specificata una query, l'elenco contiene un unico elemento denominato `[Query]`. 

**Destinazione**  
 Selezionare una tabella di destinazione dall'elenco per ogni tabella di origine o query oppure immettere il nome di una nuova tabella da creare con la procedura guidata. Se si seleziona una tabella di destinazione esistente, è necessario che la tabella abbia colonne con tipi di dati compatibili con i dati di origine.  

> [!NOTE]
> Se la procedura guidata viene sospesa a questo punto per creare manualmente una nuova tabella nel database di destinazione tramite uno strumento esterno, ad esempio  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], la nuova tabella non sarà subito visibile nell'elenco delle tabelle di destinazione disponibili. Per aggiornare l'elenco delle tabelle di destinazione, tornare indietro alla pagina **Scelta destinazione** , selezionare di nuovo il database di destinazione per aggiornare l'elenco delle tabelle e delle viste disponibili e quindi avanzare fino alla pagina **Selezione tabelle e viste di origine** .  

## <a name="optionally-review-column-mappings-and-preview-data"></a>Facoltativamente, rivedere i mapping delle colonne e visualizzare in anteprima i dati
**Modifica mapping**   
Facoltativamente, fare clic su **Modifica mapping** per visualizzare la finestra di dialogo **Mapping colonne** per la tabella selezionata. Nella finestra di dialogo **Mapping colonne** eseguire le operazioni seguenti,
-   Esaminare il mapping di singole colonne tra l'origine e la destinazione.
-   Copiare solo un subset di colonne selezionando **ignora** per le colonne da non copiare.

Per altre informazioni, vedere [Mapping colonne](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).  

**Anteprima**  
Facoltativamente, fare clic su **Anteprima** per visualizzare in anteprima fino a 200 righe di dati di esempio nella finestra di dialogo **Anteprima dati**. Questo permette di verificare che la procedura guidata sta per copiare i dati desiderati. Per altre informazioni, vedere [Anteprima dati](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md).  
  
Dopo aver visualizzato i dati in anteprima, potrebbe essere necessario modificare le opzioni selezionate nelle pagine precedenti della procedura guidata. Per apportare queste modifiche, tornare alla pagina **Seleziona tabelle e viste di origine** e quindi fare clic su **Indietro** per tornare alle pagine precedenti nelle quali modificare le opzioni selezionate.  

## <a name="select-source-and-destination-tables-for-excel"></a>Selezionare le tabelle di origine e di destinazione per Excel

### <a name="excel-source-tables"></a>Tabelle di origine Excel
L'elenco delle tabelle e delle viste di origine di un'origine dati Excel include due tipi di oggetti Excel.
-   **Fogli di lavoro**. I nomi dei fogli di lavoro sono seguiti dal segno di dollaro ($), ad esempio **'Foglio1$'**.
-   **Intervalli denominati.** Gli intervalli denominati, se presenti, sono elencati per nome.

Se si vuole caricare i dati da o in uno specifico intervallo di celle senza nome, ad esempio **[Foglio1$A1:B4]**, è necessario scrivere una query. Tornare alla pagina **Impostazione copia tabella o query** e selezionare **Scrivi una query per specificare i dati da trasferire**.

#### <a name="prepare-the-excel-source-data"></a>Preparare i dati di origine di Excel
Quando si specifica un foglio di lavoro o un intervallo come tabella di origine, il driver legge il blocco di celle *contigue* che inizia con la prima cella non vuota nell'angolo superiore sinistro del foglio di lavoro o dell'intervallo. Per questa ragione, i dati di origine non possono includere righe vuote. Ad esempio, non può essere presente una riga vuota tra le intestazioni di colonna e le righe di dati. Se è presente un titolo seguito da righe vuote nella parte superiore del foglio di lavoro sopra i dati, non è possibile eseguire query nel foglio di lavoro. In Excel è necessario assegnare un nome all'intervallo di dati ed eseguire una query nell'intervallo denominato anziché nel foglio di lavoro.

### <a name="excel-destination-tables"></a>Tabelle di destinazione Excel
Se si esportano dati in Excel, è possibile specificare la destinazione in uno dei tre modi seguenti.
-   **Foglio di lavoro.** Per specificare un foglio di lavoro, aggiungere il carattere $ alla fine del nome del foglio e aggiungere delimitatori all'inizio e alla fine della stringa, ad esempio **[Foglio1$]**.
-   **Intervallo denominato.** Per specificare un intervallo denominato, è sufficiente usare il nome dell'intervallo, ad esempio **MioIntervalloDati**.
-   **Intervallo senza nome.** Per specificare un intervallo di celle a cui non è stato assegnato un nome, aggiungere il carattere $ alla fine del nome del foglio, aggiungere la specifica dell'intervallo e aggiungere delimitatori all'inizio e alla fine della stringa, ad esempio **[Foglio1$A1:B4]**.

## <a name="special-considerations-for-excel-sources-and-destinations"></a>Considerazioni speciali per origini e destinazioni Excel
Quando si usa Excel come origine o destinazione, è consigliabile fare clic su **Modifica mapping** e rivedere i mapping dei tipi di dati nella pagina **Mapping colonne** . 

**Tipi di dati in cartelle di lavoro di Excel**. Excel non è un database tipico. Le colonne di Excel non hanno tipi di dati fissi. La procedura guidata riconosce solo un set limitato di tipi di dati in Excel: numeric, currency, Boolean, date/time, string (255 caratteri o meno) e memo (più di 255 caratteri). Per determinare il tipo di dati di ogni colonna, la procedura guidata campiona un determinato numero di righe (per impostazione predefinita, le prime otto righe) in un'origine dati Excel esistente.

Quando la procedura guidata deve eseguire conversioni esplicite dei tipi di dati per caricare i dati da o in Excel, viene in genere visualizzata la pagina **Verifica mapping tra i tipi di dati** nella quale è possibile verificare le conversioni. Le conversioni possono essere le seguenti.
-   Conversione tra colonne di Excel di tipo numerico a precisione doppia e colonne numeriche di altro tipo
-   Conversione tra colonne di Excel di tipo stringa di 255 caratteri e colonne di tipo stringa di lunghezze diverse
-   Conversione tra colonne di Excel di tipo stringa Unicode e colonne di tipo stringa non Unicode che usano tabelle codici specifiche.

### <a name="special-considerations-for-excel-sources"></a>Considerazioni speciali per le origini Excel
**Valori Null o mancanti nei dati importati**. Quando una colonna di Excel sembra contenere tipi di dati diversi nelle prime otto righe campionate, ad esempio valori di tipo numeric e di tipo text, la procedura guidata considera il tipo di dati della maggior parte dei dati come tipo di dati della colonna e restituisce valori Null per le celle contenenti dati di altri tipi. Questo funzionamento della procedura guidata non può essere modificato.

**Stringhe troncate nei dati importati**. Quando la procedura guidata individua una colonna di Excel che contiene dati di tipo text, determina il tipo di dati della colonna (string o memo) in base al valore più lungo delle prime otto righe campionate. Se la procedura guidata non individua valori contenenti più di 255 caratteri nelle righe campionate, gestirà la colonna come una colonna di stringhe di 255 caratteri anziché come una colonna con tipo di dati memo e troncherà i valori che superano i 255 caratteri. Per importare dati da una colonna memo senza troncamento, è necessario assicurarsi che la colonna di tipo memo contenga almeno un valore più lungo di 255 caratteri nelle prime otto righe campionate dalla procedura guidata.

### <a name="special-considerations-for-excel-destinations"></a>Considerazioni speciali per le destinazioni Excel
**Specifica di un intervallo esistente**. Quando si specifica un intervallo esistente come destinazione, viene visualizzato un errore se l'intervallo include meno *colonne* rispetto ai dati di origine. Tuttavia, se l'intervallo specificato include meno *righe* rispetto ai dati di origine, la procedura guidata continua la scrittura delle righe ed estende la definizione dell'intervallo in base al nuovo numero di righe.

**Salvataggio di dati memo (ntext)**. Per poter salvare correttamente stringhe di oltre 255 caratteri in una colonna Excel, la procedura guidata deve riconoscere il tipo di dati della colonna di destinazione come **memo** anziché **string**.
-   Se la tabella di destinazione contiene già righe di dati, le prime otto righe campionate dalla procedura guidata devono contenere almeno una riga con un valore più lungo di 255 caratteri nella colonna di tipo memo.
-   Se la tabella di destinazione viene creata dalla procedura guidata, l'istruzione **CREATE TABLE** deve usare **LONGTEXT** (o uno dei relativi sinonimi) come tipo di dati della colonna di tipo memo. Controllare l'istruzione **CREATE TABLE** e rivederla, se necessario, facendo clic su **Modifica SQL** accanto all'opzione **Crea tabella di destinazione** nella pagina **Mapping colonne**.

## <a name="whats-next"></a>Operazioni successive  
 Dopo aver selezionato le tabelle e le viste esistenti da copiare e sottoporre a mapping nelle rispettive destinazioni, la pagina successiva è **Salvare ed eseguire il pacchetto**. In questa pagina specificare se eseguire immediatamente l'operazione di copia. A seconda della configurazione, è anche possibile salvare il pacchetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creato dalla procedura guidata per personalizzarlo e usarlo di nuovo in seguito. Per altre informazioni, vedere [Salvare ed eseguire il pacchetto](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).
 
 ## <a name="see-also"></a>Vedere anche
[Iniziare con questo semplice esempio dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)


