---
title: Destinazione di Excel | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.exceldest.f1
- sql13.dts.designer.exceldestadapter.connection.f1
- sql13.dts.designer.exceldestadapter.mappings.f1
- sql13.dts.designer.exceldestadapter.erroroutput.f1
helpviewer_keywords:
- destinations [Integration Services], Excel
- Excel [Integration Services]
ms.assetid: 37c07446-1264-4814-b4f5-9c66d333bb24
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: 69a0a8b907fcb45cf6ecd0576fb6fba04775d237
ms.contentlocale: it-it
ms.lasthandoff: 08/17/2017

---
# <a name="excel-destination"></a>Destinazione Excel
  La destinazione Excel consente di caricare dati in fogli di lavoro o intervalli di una cartella di lavoro di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel.  
  
## <a name="access-modes"></a>Modalità di accesso  
 Sono disponibili tre diverse modalità di accesso ai dati per il caricamento dei dati:  
  
-   Vista o tabella.  
  
-   Vista o tabella specificata in una variabile.  
  
-   Risultato di un'istruzione SQL. La query può essere con parametri.  
  
> [!IMPORTANT]  
>  In Excel un intervallo o un foglio di lavoro equivale a una vista o tabella. Nell'elenco delle tabelle disponibili degli editor dell'origine e della destinazione Excel vengono visualizzati solo i fogli di lavoro (riconoscibili dalla presenza del simbolo $ in fondo al nome del foglio di lavoro, ad esempio Sheet1$) e gli intervalli denominati (riconoscibili dall'assenza del simbolo $, ad esempio MyRange) esistenti.  
  
## <a name="usage-considerations"></a>Considerazioni sull'utilizzo  
 La gestione connessione Excel usa il provider OLE DB [!INCLUDE[msCoName](../../includes/msconame-md.md)] per Jet 4.0 e il relativo driver ISAM (Indexed Sequential Access Method, metodo di accesso sequenziale indicizzato) di Excel di supporto per stabilire la connessione con le origini dati Excel, quindi leggere e scrivere informazioni.  
  
 Il comportamento di questo provider e del relativo driver è documentato in molti articoli della [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base e, sebbene tali articoli non siano specifici di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] o del suo predecessore, Data Transformation Services, consentono di ottenere informazioni circa i comportamenti che possono produrre risultati imprevisti. Per informazioni generali sull'utilizzo e sul comportamento del driver per Excel, vedere [HOWTO: Utilizzare ADO con dati di Excel da Visual Basic o VBA](http://support.microsoft.com/kb/257819).  
  
 I seguenti comportamenti del provider Jet incluso nel driver per Excel possono produrre risultati imprevisti durante il salvataggio di dati in una destinazione Excel.  
  
-   **Salvataggio di dati di testo**. Quando salva dati di testo in una destinazione Excel, il driver per Excel antepone una virgoletta singola (') al testo in ogni cella, per garantire che i valori salvati verranno interpretati come testo. Se si usano o si sviluppano altre applicazioni che leggono o elaborano i dati salvati, può essere necessario includere istruzioni specifiche per la gestione della virgoletta singola (') che precede ogni valore di testo.  
  
     Per informazioni su come evitare di includere la virgoletta singola, vedere il post di blog seguente relativo all' [aggiunta della virgoletta singola a tutte le stringhe quando i dati sono trasformati in Excel tramite il componente per flusso di dati di destinazione di Excel in un pacchetto SSIS](http://go.microsoft.com/fwlink/?LinkId=400876), su msdn.com.  
  
-   **Salvataggio di dati memo (ntext)**. Per poter salvare correttamente stringhe di oltre 255 caratteri in una colonna Excel, il driver deve riconoscere il tipo di dati della colonna di destinazione come **memo** invece di **string**. Se la tabella di destinazione contiene già righe di dati, le prime righe campionate dal driver devono contenere almeno un'istanza di un valore composto da più di 255 caratteri nella colonna con tipo di dati memo. Se la tabella di destinazione viene creata durante la progettazione del pacchetto o in fase di esecuzione, l'istruzione CREATE TABLE deve usare LONGTEXT (o uno dei sinonimi) come tipo di dati della colonna con tipo di dati memo.  
  
-   **Tipi di dati**. Il driver per Excel riconosce solo un set limitato di tipi di dati. Tutte le colonne numeriche vengono interpretate come valori double (DT_R8) e tutte le colonne di tipo stringa (con tipo di dati diverso da memo) vengono interpretate come stringhe Unicode di 255 caratteri (DT_WSTR). [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] esegue il mapping dei tipi di dati di Excel nel modo seguente:  
  
    -   Numero    Numero a virgola mobile e precisione doppia (DT_R8)  
  
    -   Valuta     Valuta (DT_CY)  
  
    -   Valore booleano     Valore booleano (DT_BOOL)  
  
    -   Data/ora     **Data/ora** (DT_DATE)  
  
    -   Stringa     Stringa Unicode di 255 caratteri (DT_WSTR)  
  
    -   Memo     Flusso di testo Unicode (DT_NTEXT)  
  
-   **Conversione di tipi di dati e lunghezze**. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] non viene eseguita la conversione implicita dei tipi di dati. Può essere pertanto necessario usare le trasformazioni Colonna derivata o Conversione dati per convertire i dati di Excel in modo esplicito prima di caricarli in una destinazione diversa da Excel oppure per convertire dati non di Excel prima di caricarli in una destinazione Excel. In questo caso può essere conveniente creare il pacchetto iniziale usando Importazione/Esportazione guidata SQL Server, che configura automaticamente le conversioni necessarie. Di seguito sono riportati alcuni esempi di tali conversioni:  
  
    -   Conversione tra colonne di Excel di tipo stringa Unicode e colonne di tipo stringa non Unicode con tabelle codici specifiche  
  
    -   Conversione tra colonne di Excel di tipo stringa di 255 caratteri e colonne di tipo stringa di lunghezze diverse  
  
    -   Conversione tra colonne di Excel di tipo numerico a precisione doppia e colonne numeriche di altro tipo  
  
## <a name="configuration-of-the-excel-destination"></a>Configurazione della destinazione Excel  
 Per connettersi a un'origine dei dati, la destinazione Excel usa una gestione connessione Excel che specifica il file di cartella di lavoro da usare. Per altre informazioni, vedere [Excel Connection Manager](../../integration-services/connection-manager/excel-connection-manager.md).  
  
 La destinazione Excel include un input regolare e un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Proprietà personalizzate di Excel](../../integration-services/data-flow/excel-custom-properties.md)  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostazione delle proprietà di un componente del flusso di dati](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-tasks"></a>Attività correlate  
  
-   [Connessione a una cartella di lavoro di Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
-   [Esecuzione di un ciclo su file e tabelle di Excel utilizzando un contenitore Ciclo Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
-   [Impostazione delle proprietà di un componente del flusso di dati](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   Intervento nel blog su [Excel in Integration Services, parte 1 di 3 relativa a connessioni e componenti](http://go.microsoft.com/fwlink/?LinkId=217674), su dougbert.com  
  
-   Intervento nel blog su [Excel in Integration Services, parte 2 di 3 relativa a tabelle e tipi di dati](http://go.microsoft.com/fwlink/?LinkId=217675), su dougbert.com.  
  
-   Intervento nel blog concernente [Excel in Integration Services, parte 3 di 3 relativa a problemi e alternative](http://go.microsoft.com/fwlink/?LinkId=217676)sul sito dougbert.com.  
  
## <a name="excel-destination-editor-connection-manager-page"></a>Editor destinazione Excel (pagina Gestione connessione)
  Utilizzare la pagina **Gestione connessione** della finestra di dialogo **Editor destinazione Excel** per specificare le informazioni sull'origine dei dati e visualizzare un'anteprima dei risultati. La destinazione Excel carica i dati in un foglio di lavoro oppure in un intervallo denominato in una cartella di lavoro di [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] .  
  
> [!NOTE]  
>  La proprietà **CommandTimeout** della destinazione Excel non è disponibile nell' **Editor destinazione Excel**, tuttavia può essere impostata utilizzando l' **Editor avanzato**. Inoltre alcune opzioni di caricamento rapido sono disponibili solamente nell' **Editor avanzato**. Per ulteriori informazioni su questa proprietà, vedere la sezione relativa alla destinazione Excel in [Excel Custom Properties](../../integration-services/data-flow/excel-custom-properties.md).  
  
### <a name="static-options"></a>Opzioni statiche  
 **Gestione connessione Excel**  
 Consente di selezionare una gestione connessione Excel esistente dall'elenco o di creare una nuova connessione facendo clic su **Nuova**.  
  
 **Nuova**  
 Consente di creare una nuova gestione connessione nella finestra di dialogo **Gestione connessione Excel** .  
  
 **Modalità di accesso ai dati**  
 Consente di specificare il metodo per la selezione dei dati dall'origine.  
  
|Opzione|Description|  
|------------|-----------------|  
|Tabella o vista|Carica i dati in un foglio di lavoro o in un intervallo denominato nell'origine dei dati di Excel.|  
|Variabile nome vista o nome tabella|Consente di specificare il foglio di lavoro o il nome dell'intervallo in una variabile.<br /><br /> **Informazioni correlate**: [Utilizzo di variabili nei pacchetti](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)|  
|Comando SQL|Consente di caricare i dati nella destinazione Excel mediante una query SQL.|  
  
 **Nome del foglio di Excel**  
 Selezionare la destinazione Excel dall'elenco a discesa. Se l'elenco è vuoto, fare clic su **Nuovo**.  
  
 **Nuova**  
 Fare clic su **Nuova** per avviare la finestra di dialogo **Crea tabella** . Quando si fa clic su **OK**viene creato il file di Excel a cui fa riferimento **Gestione connessione Excel** .  
  
 **Visualizza dati esistenti**  
 Consente di visualizzare in anteprima i risultati nella finestra di dialogo **Anteprima risultati query** . L'anteprima supporta la visualizzazione di un massimo di 200 righe.  
  
> [!WARNING]  
>  Se la **gestione connessione Excel** selezionata fa riferimento a un file di Excel che non esiste, viene visualizzato un messaggio di errore quando si fa clic su questo pulsante.  
  
### <a name="data-access-mode-dynamic-options"></a>Opzioni dinamiche relative alla modalità di accesso ai dati  
  
#### <a name="data-access-mode--table-or-view"></a>Modalità di accesso ai dati = Tabella o vista  
 **Nome del foglio di Excel**  
 Consente di selezionare il foglio di lavoro o l'intervallo denominato nell'elenco di quelli disponibili nell'origine dei dati.  
  
#### <a name="data-access-mode--table-name-or-view-name-variable"></a>Modalità di accesso ai dati = Variabile nome vista o nome tabella  
 **Nome variabile**  
 Consente di selezionare la variabile contenente il nome del foglio di lavoro o dell'intervallo denominato.  
  
#### <a name="data-access-mode--sql-command"></a>Modalità di accesso ai dati = Comando SQL  
 **Testo comando SQL**  
 Digitare il testo di una query SQL, fare clic su **Compila query**per compilare la query oppure scegliere **Sfoglia**per selezionare il file contenente il testo della query.  
  
 **Compila query**  
 Usare la finestra di dialogo **Generatore query** per creare la query SQL con strumenti grafici visuali.  
  
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per individuare il file contenente il testo della query SQL.  
  
 **Analizza query**  
 Consente di verificare la sintassi del testo della query.  
  
## <a name="excel-destination-editor-mappings-page"></a>Editor destinazione Excel (pagina Mapping)
  Utilizzare la pagina **Mapping** della finestra di dialogo **Editor destinazione Excel** per eseguire il mapping tra colonne di input e colonne di destinazione.  
  
### <a name="options"></a>Opzioni  
 **Colonne di input disponibili**  
 Consente di visualizzare l'elenco delle colonne di input disponibili. Eseguire un'operazione di trascinamento della selezione per impostare il mapping tra le colonne di input disponibili nella tabella e le colonne di destinazione.  
  
 **Colonne di destinazione disponibili**  
 Consente di visualizzare l'elenco delle colonne di destinazione disponibili. Eseguire un'operazione di trascinamento della selezione per impostare il mapping tra le colonne di destinazione disponibili nella tabella e le colonne di input.  
  
 **Colonna di input**  
 Consente di visualizzare le colonne di input selezionate nella tabella precedente. È possibile modificare i mapping utilizzando l'elenco **Colonne di input disponibili**.  
  
 **Colonna di destinazione**  
 Consente di visualizzare tutte le colonne di destinazione disponibili, indipendentemente dal fatto che siano mappate o meno.  
  
## <a name="excel-destination-editor-error-output-page"></a>Editor destinazione Excel (pagina Output degli errori)
  Usare la pagina **Avanzate** della finestra di dialogo **Editor destinazione Excel** per specificare le opzioni per la gestione degli errori.  
  
### <a name="options"></a>Opzioni  
 **Input o output**  
 Consente di visualizzare il nome dell'origine dei dati.  
  
 **Colonna**  
 Consente di visualizzare le colonne esterne (di origine) selezionate nel nodo **Gestione connessione** della finestra di dialogo **Editor origine Excel**.  
  
 **Errore**  
 Consente di specificare l'azione da eseguire in caso di errori, ovvero ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
 **Argomenti correlati:** [Gestione degli errori nei dati](../../integration-services/data-flow/error-handling-in-data.md)  
  
 **Troncamento**  
 Consente di specificare l'azione da eseguire in caso di troncamenti, ovvero ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
 **Description**  
 Consente di visualizzare la descrizione dell'errore.  
  
 **Imposta questo valore nelle celle selezionate**  
 Consente di specificare l'azione che dovrà interessare tutte le celle selezionate in caso di errore o troncamento: ignorare l'errore, reindirizzare la riga o interrompere il componente.  
  
 **Applica**  
 Consente di applicare l'opzione di gestione degli errori alle celle selezionate.  
  
## <a name="see-also"></a>Vedere anche  
 [Origine Excel](../../integration-services/data-flow/excel-source.md)   
 [Integration Services &#40; SSIS &#41; Variabili](../../integration-services/integration-services-ssis-variables.md)   
 [Flusso di dati](../../integration-services/data-flow/data-flow.md)   
 [Utilizzo dei file di Excel con l'attività Script](../../integration-services/extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
  
  
