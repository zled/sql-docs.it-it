---
title: "Pulire i dati mediante le informazioni dei dati di riferimento (esterni) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 158009e9-8069-4741-8085-c14a5518d3fc
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# Pulire i dati mediante le informazioni dei dati di riferimento (esterni)
  In questo argomento viene descritto come pulire i dati utilizzando le informazioni dei provider di dati di riferimento. Mentre tutti i passaggi di eseguire un'attività di pulizia rimane lo stesso di pulizia dei dati utilizzando le informazioni dei provider di dati di riferimento come illustrato nella [pulire i dati tramite DQS & #40; interno & #41; Knowledge Base](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md), in questo argomento fornisce informazioni specifiche per la pulizia dei dati tramite il servizio dati di riferimento in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
 Quando in DQS si utilizza la funzionalità del servizio dati di riferimento per pulire i dati, il processo di pulizia di DQS invia i valori di dominio di cui è stato eseguito il mapping al provider del servizio dati di riferimento come richiesta batch. Il servizio dati di riferimento risponde con le informazioni seguenti:  
  
-   Correzione suggerita  
  
-   Confidenza  
  
-   Informazioni aggiuntive sul dominio di cui è stato eseguito il mapping. I dati di riferimento possono inoltre standardizzare, analizzare o migliorare l'origine con dati aggiuntivi. Tali informazioni vengono fornite nei campi aggiuntivi della risposta.  
  
 Dopo avere ottenuto la risposta dal servizio dati di riferimento, durante l'attività di pulizia in DQS si verifica quanto segue:  
  
-   In base ai valori **Soglia di correzione automatica** e **Confidenza min** specificati durante l'esecuzione del mapping dei domini con il servizio dati di riferimento, i valori di dominio vengono suggeriti o corretti automaticamente in base al livello di confidenza.  
  
    > [!NOTE]  
    >  Durante la pulizia dei dati mediante le informazioni del servizio dati di riferimento vengono applicati i valori soglia specificati al momento dell'esecuzione del mapping di un dominio a un servizio dati di riferimento e non i valori specificati nella scheda **Impostazioni generali** della sezione **Configurazione** . Per informazioni su come specificare i valori di soglia per la pulizia dei dati di riferimento, vedere il passaggio 9 in [collegare dominio o dominio composito ai dati di riferimento](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md).  
  
-   I valori di dominio vengono suddivisi nelle categorie seguenti: **Suggeriti**, **Nuovi**, **Non validi**, **Con correzione**e **Corretti**.  
  
-   I dati aggiuntivi vengono aggiunti all'origine e le informazioni sono disponibili insieme ai dati puliti per l'esportazione.  
  
## Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 È necessario avere eseguito il mapping dei domini richiesti in una Knowledge Base DQS al servizio dati di riferimento appropriato. La Knowledge Base deve inoltre contenere informazioni sul tipo di dati da pulire. Se si desidera pulire dati di origine che contengono indirizzi US, ad esempio, è necessario eseguire il mapping dei domini a un provider del servizio dati di riferimento che fornisce dati di alta qualità per gli indirizzi US. Per ulteriori informazioni, vedere [collegare dominio o dominio composito ai dati di riferimento](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per eseguire la pulizia dei dati è necessario disporre del ruolo dqs_kb_editor o dqs_kb_operator nel database DQS_MAIN.  
  
##  <a name="Cleanse"></a> Pulire i dati mediante le informazioni dei dati di riferimento  
 Si continuerà con lo stesso esempio di utilizzo dei domini che è stato eseguito il mapping nell'argomento precedente, [collegare dominio o dominio composito ai dati di riferimento](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md), con il servizio Melissa Data in Windows Azure Marketplace. Vengono utilizzati gli stessi domini per pulire alcuni indirizzi US di esempio. I passaggi per pulire i dati sono identico a quello descritto [pulire i dati tramite DQS & #40; interno & #41; Knowledge Base](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md). Eventuali differenze verranno indicate durante il processo, laddove necessario.  
  
1.  Creare un progetto Data Quality e selezionare l'attività **Pulizia** . Vedere [Create a Data Quality Project](../data-quality-services/create-a-data-quality-project.md).  
  
2.  Nella pagina **Mappa** eseguire il mapping dei 4 domini seguenti con le colonne appropriate nei dati di origine: **Riga indirizzo**, **Città**, **Stato**e **CAP**. Scegliere **Avanti**.  
  
    > [!NOTE]  
    >  Come è stato eseguito il mapping di tutti i 4 domini all'interno di **Verifica indirizzo** dominio composito, la pulizia dei dati verrà eseguita a livello di dominio composito e non a livello di singolo dominio.  
  
3.  Nel **Pulisci** pagina, eseguita il processo di pulizia computerizzato facendo **avviare**. Al termine del processo di pulizia, fare clic su **Avanti**.  
  
    > [!NOTE]  
    >  Nel **Pulisci** pagina, vengono visualizzate le informazioni sui domini collegati servizio dati di riferimento negli elementi seguenti in due modi:  
    >   
    >  -   Di seguito viene visualizzato un messaggio di **avviare** pulsante: "domini \< dominio1>, \< dominio2>,... \< Dominion> vengono puliti utilizzando il provider del servizio dati di riferimento. " In questo esempio verrà visualizzato il messaggio seguente: "La verifica dell'indirizzo del dominio viene pulita usando il provider del servizio dati di riferimento".  
    > -   Un'icona, ![Dominio collegato al servizio dati di riferimento](../data-quality-services/media/dqs-rdsindicator.png "Dominio collegato al servizio dati di riferimento"), viene visualizzato nel **Profiler** area rispetto ai domini collegati al provider del servizio dati di riferimento. Nell'esempio l'icona verrà visualizzata per il dominio composito **Verifica indirizzo** .  
  
4.  Verificare i valori di dominio nella pagina **Gestisci e visualizza i risultati** . Il servizio dati di riferimento può visualizzare più suggerimenti, se disponibili, per un valore a seconda del numero massimo di suggerimenti specificato nella casella **Candidati suggeriti** durante l'esecuzione del mapping del dominio al servizio dati di riferimento. Per l'indirizzo US seguente vengono visualizzati, ad esempio, due suggerimenti:  
  
     **Valore originale:**  
  
    |Riga indirizzo|Città|Stato|CAP|  
    |------------------|----------|-----------|---------|  
    |1 msft way|Redmond||98052|  
  
     **Valori suggeriti:**  
  
    |Riga indirizzo|Città|Stato|CAP|  
    |------------------|----------|-----------|---------|  
    |1 Microsoft Way|Redmond|WA|98052|  
    |PO Box 1|Redmond|WA|98073|  
  
     ![Pulizia tramite il servizio dati di riferimento](../data-quality-services/media/dqs-rdscleansing.JPG "Pulizia tramite il servizio dati di riferimento")  
  
    > [!NOTE]  
    >  Per i domini compositi vengono evidenziati in un colore diverso anche i singoli domini corretti durante il processo di pulizia computerizzato. In questo caso, ad esempio, sono stati corretti i domini **Riga indirizzo** e **Stato** che pertanto vengono evidenziati in ciano.  
  
5.  Dopo avere verificato tutti i valori di dominio, fare clic su **Avanti** per esportare i dati.  
  
6.  Nel **esportare** pagina, si noterà che oltre a informazioni normali attività di pulizia per ogni dominio (origine, motivo, confidenza e stato), vi sono ulteriori informazioni forniti da riferimento Melissa Data servizio dati sui dati di indirizzo, ad esempio latitudine e longitudine di indirizzo, nome della provincia, indirizzo digitare (palazzo a molti piani, strada, ecc.) e così via.  
  
7.  Esportare i dati nella destinazione richiesta (SQL Server, CSV o Excel) e fare clic su **Fine** per chiudere il progetto.  
  
    > [!IMPORTANT]  
    >  Se si utilizza la versione a 64 bit di Excel, non è possibile esportare i dati puliti in un file di Excel. È possibile eseguire l'esportazione solo in un database di SQL Server o in un file con estensione csv.  
  
  