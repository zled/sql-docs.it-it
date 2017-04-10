---
title: "Editor destinazione Excel (pagina Gestione connessione) | Microsoft Docs"
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
  - "sql13.dts.designer.exceldestadapter.connection.f1"
helpviewer_keywords: 
  - "Editor destinazione Excel"
ms.assetid: fc13f725-963c-488e-91e2-20627133e842
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# Editor destinazione Excel (pagina Gestione connessione)
  Utilizzare la pagina **Gestione connessione** della finestra di dialogo **Editor destinazione Excel** per specificare le informazioni sull'origine dei dati e visualizzare un'anteprima dei risultati. La destinazione Excel carica i dati in un foglio di lavoro oppure in un intervallo denominato in una cartella di lavoro di [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] .  
  
> [!NOTE]  
>  La proprietà **CommandTimeout** della destinazione Excel non è disponibile nell' **Editor destinazione Excel**, tuttavia può essere impostata utilizzando l' **Editor avanzato**. Inoltre alcune opzioni di caricamento rapido sono disponibili solamente nell' **Editor avanzato**. Per ulteriori informazioni su questa proprietà, vedere la sezione relativa alla destinazione Excel in [Excel Custom Properties](../../integration-services/data-flow/excel-custom-properties.md).  
  
 Per ulteriori informazioni sulla destinazione Excel, vedere [Excel Destination](../../integration-services/data-flow/excel-destination.md).  
  
## Opzioni statiche  
 **Gestione connessione Excel**  
 Consente di selezionare una gestione connessione Excel esistente dall'elenco o di creare una nuova connessione facendo clic su**Nuova**.  
  
 **Nuova**  
 Consente di creare una nuova gestione connessione nella finestra di dialogo **Gestione connessione Excel**.  
  
 **Modalità di accesso ai dati**  
 Consente di specificare il metodo per la selezione dei dati dall'origine.  
  
|Opzione|Description|  
|------------|-----------------|  
|Tabella o vista|Carica i dati in un foglio di lavoro o in un intervallo denominato nell'origine dei dati di Excel.|  
|Variabile nome vista o nome tabella|Consente di specificare il foglio di lavoro o il nome dell'intervallo in una variabile.<br /><br /> **Informazioni correlate**: [Utilizzo di variabili nei pacchetti](../Topic/Use%20Variables%20in%20Packages.md)|  
|Comando SQL|Consente di caricare i dati nella destinazione Excel mediante una query SQL.|  
  
 **Nome del foglio di Excel**  
 Selezionare la destinazione Excel dall'elenco a discesa. Se l'elenco è vuoto, fare clic su **Nuovo**.  
  
 **Nuova**  
 Fare clic su **Nuova** per avviare la finestra di dialogo **Crea tabella**. Quando si fa clic su **OK**viene creato il file di Excel a cui fa riferimento **Gestione connessione Excel** .  
  
 **Visualizza dati esistenti**  
 Consente di visualizzare in anteprima i risultati nella finestra di dialogo **Anteprima risultati query**. L'anteprima supporta la visualizzazione di un massimo di 200 righe.  
  
> [!WARNING]  
>  Se la **gestione connessione Excel** selezionata fa riferimento a un file di Excel che non esiste, viene visualizzato un messaggio di errore quando si fa clic su questo pulsante.  
  
## Opzioni dinamiche relative alla modalità di accesso ai dati  
  
### Modalità di accesso ai dati = Tabella o vista  
 **Nome del foglio di Excel**  
 Consente di selezionare il foglio di lavoro o l'intervallo denominato nell'elenco di quelli disponibili nell'origine dei dati.  
  
### Modalità di accesso ai dati = Variabile nome vista o nome tabella  
 **Nome variabile**  
 Consente di selezionare la variabile contenente il nome del foglio di lavoro o dell'intervallo denominato.  
  
### Modalità di accesso ai dati = Comando SQL  
 **Testo comando SQL**  
 Digitare il testo di una query SQL, fare clic su **Compila query** per compilare la query oppure scegliere **Sfoglia** per selezionare il file contenente il testo della query.  
  
 **Compila query**  
 Usare la finestra di dialogo **Generatore query** per creare la query SQL con strumenti grafici visuali.  
  
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per individuare il file contenente il testo della query SQL.  
  
 **Analizza query**  
 Consente di verificare la sintassi del testo della query.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor destinazione Excel &#40;pagina Mapping&#41;](../../integration-services/data-flow/excel-destination-editor-mappings-page.md)   
 [Editor destinazione Excel &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/excel-destination-editor-error-output-page.md)   
 [Esecuzione di un ciclo su file e tabelle di Excel utilizzando un contenitore Ciclo Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  