---
title: "Apertura di progetti di Integration Services nel client Data Quality | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Apertura di progetti di Integration Services nel client Data Quality
  Il componente pulizia DQs in Integration Services consente di eseguire un progetto di pulizia in modalità batch. Tuttavia, a volte è necessario rivedere i risultati della pulizia in un pacchetto di Integration Services simile a come è possibile esaminare i risultati della pulizia nel **Gestisci e Visualizza risultati** della scheda di un'attività di pulizia in un progetto data quality in DQS. DQS consente di aprire i progetti di Integration Services in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] esattamente come qualsiasi altro progetto data quality dal **Apri progetto** e di eseguire attività interattive sui risultati della pulizia in un progetto di Integration Services.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
  
-   Solo i progetti sono disponibili in Integration Services completati il **Apri progetto** nella schermata [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Non sono disponibili in progetti non riusciti o è in esecuzione il **Apri progetto** dello schermo.  
  
-   Aprire progetti di Integration Services in fase di pulizia interattiva (**Gestione Vista e risultati** scheda) in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. È possibile accedere al **Pulisci** o **mappa** schede. È possibile utilizzare solo il **esportare** facendo clic **Avanti**.  
  
-   Non è possibile eliminare un progetto di Integration Services bloccato da [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. È necessario procedere allo sblocco prima dell'eliminazione.  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 È necessario che sia completata l'esecuzione di un progetto di Integration Services contenente un pacchetto con un componente di pulizia di DQS per vedere e aprirlo in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Per aprire un progetto di Integration Services è necessario disporre del ruolo dqs_kb_editor o dqs_kb_operator nel database DQS_MAIN.  
  
  
##  <a name="Open"></a> Apertura di un progetto di Integration Services  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Client Data Quality](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nel [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] schermata iniziale fare clic su **Apri progetto Data Quality**. Verrà visualizzata la finestra di dialogo **Apri progetto** .  
  
3.  Nel **Apri progetto** dello schermo, è possibile identificare un progetto di Integration Services in uno dei modi seguenti:  
  
    1.  **Nome del progetto**: progetti di Integration Services sono elencati utilizzando la terminologia di denominazione seguente: "package DQS*\< data>**\< ora>*_ {GUID}." Ogni volta che si esegue correttamente il pacchetto stesso [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], un nuovo progetto è elencato nel **Apri progetto** dello schermo.  
  
    2.  **Tipo di progetto**: i progetti di Integration Services hanno **SSIS** come tipo di progetto nel **Apri progetto** dello schermo.  
  
     Selezionare un progetto, quindi fare clic su **Avanti**.  
  
4.  Verrà aperto il progetto di Integration Services in fase di pulizia interattiva (**Gestione Vista e risultati** scheda). È possibile eseguire una pulizia interattiva sui dati nel progetto di Integration Services. Per informazioni dettagliate di **Gestisci e Visualizza risultati** scheda, vedere [fase di pulizia interattiva](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive) in [pulire i dati tramite DQS &#40; interno &#41; Knowledge Base](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).  
  
5.  Fare clic su **successivo** per visualizzare il **esportare** scheda in cui è possibile esportare i dati elaborati in uno dei seguenti: una nuova tabella nel database di SQL Server, un file con estensione csv o un file di Excel. Per informazioni dettagliate di **esportare** scheda, vedere [fase di esportazione](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export) in [pulire i dati tramite DQS &#40; interno &#41; Knowledge Base](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
6.  Dopo avere esportato i dati, fare clic su **Fine** per chiudere il progetto di Integration Services.  

  
## Vedere anche  
 [Trasformazione DQS Cleansing](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)   
 [Integration Services (SSIS) progetti](https://msdn.microsoft.com/library/ms138028.aspx)  
  
  