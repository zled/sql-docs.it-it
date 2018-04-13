---
title: Origine Excel | Microsoft Docs
ms.custom: ''
ms.date: 04/02/2018
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: ''
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.dts.designer.excelsource.f1
- sql13.dts.designer.excelsourceadapter.connection.f1
- sql13.dts.designer.excelsourceadapter.columns.f1
- sql13.dts.designer.excelsourceadapter.erroroutput.f1
helpviewer_keywords:
- Excel [Integration Services]
- sources [Integration Services], Excel
ms.assetid: e66349f3-b1b8-4763-89b7-7803541a4d62
caps.latest.revision: 60
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6a9795de30c7d4fbe2ede9a17043a916e5953cd5
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="excel-source"></a>Origine Excel
  L'origine Excel consente di estrarre dati da fogli di lavoro o intervalli di una cartella di lavoro di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel.  

> [!IMPORTANT]
> Per informazioni dettagliate sulla connessione ai file di Excel e sulle limitazioni e i problemi noti per il caricamento di dati da o a file di Excel, vedere [Caricare i dati da o in Excel con SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md).

## <a name="access-mode"></a>Modalità di accesso
 Sono disponibili quattro diverse modalità di accesso ai dati per l'estrazione dei dati:  
  
-   Vista o tabella.  
  
-   Vista o tabella specificata in una variabile.  
  
-   Risultato di un'istruzione SQL. La query può essere con parametri.  
  
-   Risultato di un'istruzione SQL archiviata in una variabile.  
  
 Per connettersi a un'origine dei dati l'origine Excel utilizza una gestione connessione Excel che specifica il file di cartella di lavoro da utilizzare. Per altre informazioni, vedere [Excel Connection Manager](../../integration-services/connection-manager/excel-connection-manager.md).  
  
 L'origine Excel include un output regolare e un output degli errori.  
  
## <a name="usage-considerations"></a>Considerazioni sull'utilizzo  
 La gestione connessione Excel usa il provider OLE DB [!INCLUDE[msCoName](../../includes/msconame-md.md)] per Jet 4.0 e il relativo driver ISAM (Indexed Sequential Access Method, metodo di accesso sequenziale indicizzato) di Excel di supporto per stabilire la connessione con le origini dati Excel, quindi leggere e scrivere informazioni.  
  
 Il comportamento di questo provider e del relativo driver è documentato in molti articoli della [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base e, sebbene tali articoli non siano specifici di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] o del suo predecessore, Data Transformation Services, consentono di ottenere informazioni circa i comportamenti che possono produrre risultati imprevisti. Per informazioni generali sull'utilizzo e sul comportamento del driver per Excel, vedere [HOWTO: Utilizzare ADO con dati di Excel da Visual Basic o VBA](http://support.microsoft.com/kb/257819).  
  
 I seguenti comportamenti del provider Jet utilizzato insieme al driver per Excel possono produrre risultati imprevisti durante la lettura da un'origine dei dati Excel.  
  
-   **Origini dei dati**. L'origine dei dati in una cartella di lavoro di Excel può essere un foglio di lavoro, a cui è necessario aggiungere il simbolo $, ad esempio Sheet1$ o un intervallo denominato, ad esempio MyRange. Nelle istruzioni SQL i nomi dei fogli di lavoro devono essere delimitati (ad esempio, [Sheet1$]) per evitare errori di sintassi dovuti alla presenza del simbolo $. In Generatore query tali delimitatori vengono aggiunti automaticamente. Quando si specifica un foglio di lavoro o un intervallo, il driver legge il blocco di celle contigue che inizia con la prima cella non vuota nell'angolo superiore sinistro del foglio di lavoro o dell'intervallo. Non è pertanto possibile utilizzare origini contenenti righe vuote tra i dati oppure tra il titolo o le righe di intestazione e le righe di dati.  
  
-   **Valori mancanti**. Per determinare il tipo di dati di ogni colonna, il driver per Excel legge un determinato numero di righe (8 per impostazione predefinita) nell'origine specificata. Se una colonna contiene tipi di dati diversi, soprattutto se sono presenti sia dati numerici che di testo, il driver adotta il tipo di dati a cui corrisponde il maggior numero di elementi e restituisce valori Null per le celle che contengono dati di tipo diverso. In caso di parità, viene adottato il tipo numerico. La maggior parte delle opzioni di formattazione utilizzate nei fogli di lavoro di Excel non influisce sulla determinazione del tipo di dati. È possibile modificare questo comportamento del driver per Excel specificando la Modalità di importazione. Per specificare la Modalità di importazione, aggiungere **IMEX=1** al valore di Proprietà estese nella stringa di connessione della gestione connessione Excel nella finestra **Proprietà** . Per altre informazioni, vedere l'articolo relativo a [PRB sui valori di Excel restituiti come NULL tramite OpenRecordset DAO](http://support.microsoft.com/kb/194124).  
  
-   **Testo troncato**. Se il driver determina che una colonna di Excel contiene dati di tipo text, seleziona il tipo di dati (string o memo), in base al più lungo valore campionato. Se il driver non individua valori contenenti più di 255 caratteri nelle righe campionate, gestirà la colonna come una colonna di stringhe di 255 caratteri, anziché come una colonna con tipo di dati memo. I valori contenenti più di 255 caratteri potrebbero essere pertanto troncati. Per evitare troncamenti durante l'importazione di dati da una colonna di tipo memo, è necessario verificare che almeno una delle righe campionate nella colonna di tipo memo contenga un valore con più di 255 caratteri oppure aumentare il numero delle righe campionate dal driver, in modo da includere una riga di questo tipo. È possibile aumentare il numero di righe campionate incrementando il valore di **TypeGuessRows** sotto la chiave del Registro di sistema **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** . Per altre informazioni, vedere l'articolo relativo a [PRB sul trasferimento di dati dall'origine Jet 4.0 OLEDB che non si effettua con l'errore di buffer di overflow](http://support.microsoft.com/kb/281517).  
  
-   **Tipi di dati**. Il driver per Excel riconosce solo un set limitato di tipi di dati. Tutte le colonne numeriche vengono interpretate come valori double (DT_R8) e tutte le colonne di tipo stringa (con tipo di dati diverso da memo) vengono interpretate come stringhe Unicode di 255 caratteri (DT_WSTR). [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] esegue il mapping dei tipi di dati di Excel nel modo seguente:  
  
    -   Numero – Numero a virgola mobile e precisione doppia (DT_R8)  
  
    -   Valuta - Valuta (DT_CY)  
  
    -   Valore booleano - Valore booleano (DT_BOOL)  
  
    -   Data/ora - **datetime** (DT_DATE)  
  
    -   Stringa - Stringa Unicode di 255 caratteri (DT_WSTR)  
  
    -   Memo - Flusso di testo Unicode (DT_NTEXT)  
  
-   **Conversione di tipi di dati e lunghezze**. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] non viene eseguita la conversione implicita dei tipi di dati. Può essere pertanto necessario utilizzare trasformazioni Colonna derivata o Conversione dati per convertire i dati di Excel in modo esplicito prima di caricarli in una destinazione diversa da Excel oppure per convertire dati non di Excel prima di caricarli in una destinazione Excel. In questo caso può essere conveniente creare il pacchetto iniziale usando Importazione/Esportazione guidata SQL Server, che configura automaticamente le conversioni necessarie. Di seguito sono riportati alcuni esempi di tali conversioni:  
  
    -   Conversione tra colonne di Excel di tipo stringa Unicode e colonne di tipo stringa non Unicode con tabelle codici specifiche  
  
    -   Conversione tra colonne di Excel di tipo stringa di 255 caratteri e colonne di tipo stringa di lunghezze diverse  
  
    -   Conversione tra colonne di Excel di tipo numerico a precisione doppia e colonne numeriche di altro tipo  
  
## <a name="excel-source-configuration"></a>Configurazione dell'origine Excel  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Proprietà personalizzate di Excel](../../integration-services/data-flow/excel-custom-properties.md)  
  
 Per informazioni sul ciclo tramite un gruppo di file Excel, vedere [Esecuzione di un ciclo su file e tabelle di Excel utilizzando un contenitore Ciclo Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Mapping dei parametri di query a variabili in un componente del flusso di dati](../../integration-services/data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [Impostazione delle proprietà di un componente del flusso di dati](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [Ordinamento dei dati per le trasformazioni Unione e Merge Join](../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
-   [Esecuzione di un ciclo su file e tabelle di Excel usando un contenitore Ciclo Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
## <a name="excel-source-editor-connection-manager-page"></a>Editor origine Excel (pagina Gestione connessione)
  Usare il nodo **Gestione connessione** della finestra di dialogo **Editor origine Excel** per selezionare la cartella di lavoro di [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] da usare come origine. L'origine Excel legge i dati da un foglio di lavoro o da un intervallo denominato in una cartella di lavoro esistente.  
  
> [!NOTE]  
>  La proprietà **CommandTimeout** dell'origine Excel non è disponibile nell' **Editor origine Excel**, tuttavia può essere impostata usando l' **Editor avanzato**. Per altre informazioni su questa proprietà, vedere la sezione relativa all'origine Excel in [Proprietà personalizzate di Excel](../../integration-services/data-flow/excel-custom-properties.md).  
  
### <a name="static-options"></a>Opzioni statiche  
 **Gestione connessione OLE DB**  
 Consente di selezionare una gestione connessione Excel esistente dall'elenco o di creare una nuova connessione facendo clic su **Nuova**.  
  
 **Nuova**  
 Consente di creare una nuova gestione connessione nella finestra di dialogo **Gestione connessione Excel** .  
  
 **Modalità di accesso ai dati**  
 Consente di specificare il metodo per la selezione dei dati dall'origine.  
  
|valore|Description|  
|-----------|-----------------|  
|Tabella o vista|Consente di recuperare dati da un foglio di lavoro o da un intervallo denominato nel file di Excel.|  
|Variabile nome vista o nome tabella|Consente di specificare il foglio di lavoro o il nome dell'intervallo in una variabile.<br /><br /> **Informazioni correlate:** [Utilizzo di variabili nei pacchetti](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)|  
|Comando SQL|Consente di recuperare dati dal file di Excel utilizzando una query SQL. |  
|Comando SQL da variabile|Consente di specificare il testo della query SQL in una variabile.|  
  
 **Anteprima**  
 Consente di visualizzare in anteprima i risultati nella finestra di dialogo **Vista dati** . L'anteprima supporta la visualizzazione di un massimo di 200 righe.  
  
### <a name="data-access-mode-dynamic-options"></a>Opzioni dinamiche relative alla modalità di accesso ai dati  
  
#### <a name="data-access-mode--table-or-view"></a>Modalità di accesso ai dati = Tabella o vista  
 **Nome del foglio di Excel**  
 Consente di selezionare il nome del foglio di lavoro o dell'intervallo denominato in un elenco di fogli di lavoro o intervalli disponibili nella cartella di lavoro di Excel.  
  
#### <a name="data-access-mode--table-name-or-view-name-variable"></a>Modalità di accesso ai dati = Variabile nome vista o nome tabella  
 **Nome variabile**  
 Consente di selezionare la variabile contenente il nome del foglio di lavoro o dell'intervallo denominato.  
  
#### <a name="data-access-mode--sql-command"></a>Modalità di accesso ai dati = Comando SQL  
 **Testo comando SQL**  
 È possibile digitare il testo di una query SQL, compilare la query facendo clic su **Compila query**o cercare il file contenente il testo della query facendo clic su **Sfoglia**.  
  
 **Parametri**  
 Se è stata immessa una query con parametri utilizzando ? come segnaposto per il parametro nel testo della query, usare la finestra di dialogo **Imposta parametri query** per eseguire il mapping tra i parametri di input della query e le variabili del pacchetto.  
  
 **Build query**  
 Usare la finestra di dialogo **Generatore query** per creare la query SQL con strumenti grafici.  
  
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per individuare il file contenente il testo della query SQL.  
  
 **Analizza query**  
 Consente di verificare la sintassi del testo della query.  
  
#### <a name="data-access-mode--sql-command-from-variable"></a>Modalità di accesso ai dati = Comando SQL da variabile  
 **Nome variabile**  
 Consente di selezionare la variabile contenente il testo della query SQL.  
  
## <a name="excel-source-editor-columns-page"></a>Editor origine Excel (pagina Colonne)
  Usare la pagina **Colonne** della finestra di dialogo **Editor origine Excel** per eseguire il mapping tra una colonna di output e ogni colonna (di origine) esterna.  
  
### <a name="options"></a>Opzioni  
 **Colonne esterne disponibili**  
 Consente di visualizzare l'elenco delle colonne esterne disponibili nell'origine dei dati. Non è possibile utilizzare questa tabella per l'aggiunta o l'eliminazione di colonne.  
  
 **Colonna esterna**  
 Consente di visualizzare le colonne esterne (origine) nell'ordine in cui verranno lette dall'attività. È possibile modificare l'ordine deselezionando innanzitutto le colonne selezionate nella tabella sopra descritta e quindi selezionando le colonne esterne nell'elenco secondo un ordine diverso.  
  
 **Colonna di output**  
 Consente di specificare un nome univoco per ogni colonna di output. Per impostazione predefinita viene suggerito il nome della colonna esterna (di origine) selezionata. È comunque possibile scegliere qualsiasi nome descrittivo univoco. Il nome specificato verrà visualizzato in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
## <a name="excel-source-editor-error-output-page"></a>Editor origine Excel (pagina Output degli errori)
  Usare la pagina **Output degli errori** della finestra di dialogo **Editor origine Excel** per selezionare le opzioni di gestione degli errori e impostare le proprietà delle colonne di output degli errori.  
  
### <a name="options"></a>Opzioni  
 **Input o output**  
 Consente di visualizzare il nome dell'origine dei dati.  
  
 **Colonna**  
 Consente di visualizzare le colonne esterne (di origine) selezionate nella pagina **Gestione connessione** della finestra di dialogo **Editor origine Excel**.  
  
 **Errore**  
 Consente di specificare l'azione da eseguire in caso di errori, ovvero ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
 **Argomenti correlati:** [Gestione degli errori nei dati](../../integration-services/data-flow/error-handling-in-data.md)  
  
 **Troncamento**  
 Consente di specificare l'azione da eseguire in caso di troncamenti, ovvero ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
 **Descrizione**  
 Consente di visualizzare la descrizione dell'errore.  
  
 **Imposta questo valore nelle celle selezionate**  
 Consente di specificare l'azione che dovrà interessare tutte le celle selezionate in caso di errore o troncamento: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
 **Applica**  
 Consente di applicare l'opzione di gestione degli errori alle celle selezionate.  
  
## <a name="related-content"></a>Contenuto correlato  
[Caricare i dati da o in Excel con SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)
[Destinazione Excel](excel-destination.md)  
[Gestione connessione Excel](../connection-manager/excel-connection-manager.md)
