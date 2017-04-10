---
title: "Creare una Knowledge Base | Microsoft Docs"
ms.custom: ""
ms.date: "06/04/2013"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.kb.selectkb.f1"
  - "sql13.dqs.kb.newkb.f1"
ms.assetid: 2733a284-975f-4650-abcc-cc2aad074cab
caps.latest.revision: 20
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# Creare una Knowledge Base
  In questo argomento viene descritto come creare una Knowledge Base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) e prepararla per le attività di gestione del dominio, individuazione delle informazioni o aggiunta di criteri di corrispondenza.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Per creare una Knowledge Base, è necessario avere installato il [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] e il [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per creare una Knowledge Base, è necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN.  
  
##  <a name="Createaknowledgebase"></a> Creare una Knowledge Base  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Client Data Quality](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] fare clic su **Nuova Knowledge Base**.  
  
3.  Immettere un nome e una descrizione per la nuova Knowledge Base.  
  
4.  In **Crea Knowledge Base da**selezionare l'elemento sui cui basare la Knowledge Base.  
  
    -   Selezionare **Nessuno** se non si desidera basare la nuova Knowledge Base su una Knowledge Base esistente o su un file di dati.  
  
    -   Selezionare **Knowledge Base esistente** per basare la nuova Knowledge Base su una Knowledge Base già creata nel [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]o sulla Knowledge Base predefinita. Selezionare la knowledge base dal **Selezionare Knowledge Base** elenco a discesa o fare clic su **Sfoglia** per visualizzare il **Selezionare una Knowledge Base** nella finestra di dialogo scegliere una conoscenze base su cui basare la nuova knowledge base e quindi fare clic su **OK**. Quando si seleziona una Knowledge Base dalla tabella, i domini e le regole di corrispondenza nella Knowledge Base verranno visualizzati nel riquadro a destra della finestra di dialogo. È inoltre possibile selezionare il **dati DQS** della knowledge base, ovvero la knowledge base predefinita che contiene domini comuni out-of-the-box e le informazioni correlate a società, indirizzo e dati di entità degli Stati Uniti.  
  
    -   Selezionare **Importa da file DQS** per basare la nuova Knowledge Base su un file DQS nel [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]. Fare clic su **Sfoglia**, selezionare un file di dati DQS con un'estensione DQS, quindi fare clic su **OK**.  
  
5.  In **Seleziona attività**selezionare l'attività che si desidera eseguire sulla nuova Knowledge Base:  
  
    -   Selezionare **Gestione dominio** per creare la Knowledge Base e visualizzare le schermate per la modifica dei domini nella Knowledge Base.  
  
    -   Selezionare **Individuazione informazioni** per creare la Knowledge Base e avviare la procedura guidata che consente di analizzare un campione di dati e di popolare i domini della Knowledge Base con i risultati.  
  
    -   Selezionare **Criteri di corrispondenza** per creare criteri di corrispondenza e aggiungerli alla Knowledge Base.  
  
6.  Fare clic su **Crea**.  
  
##  <a name="FollowUp"></a> Completamento: fasi successive alla creazione di una Knowledge Base  
 Dopo avere creato una Knowledge Base, vengono visualizzate una procedura guidata che consente di eseguire l'individuazione delle informazioni, una procedura guidata per creare i criteri di corrispondenza o le pagine per eseguire la gestione del dominio. Per ulteriori informazioni sui criteri di corrispondenza, l'individuazione delle informazioni o gestione del dominio, vedere [eseguire l'individuazione delle informazioni](../data-quality-services/perform-knowledge-discovery.md), [gestione di un dominio](../data-quality-services/managing-a-domain.md), o [creare criteri di corrispondenza](../data-quality-services/create-a-matching-policy.md).  
  
  