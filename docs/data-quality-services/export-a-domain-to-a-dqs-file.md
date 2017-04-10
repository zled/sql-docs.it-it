---
title: "Esportazione di un dominio in un file DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eba10d3d-b5c4-447b-8a30-fa07996cb28e
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 18
---
# Esportazione di un dominio in un file DQS
  In questo argomento viene descritto come esportare un dominio in un file DQS [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). È possibile esportare un dominio o una Knowledge Base intera in un file di dati. Per informazioni sull'esportazione di una knowledge base, vedere [esportare una Knowledge Base in un File DQS](../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md).  
  
 L'esportazione di un dominio da una Knowledge Base a un file di dati DQS e la successiva importazione in un'altra semplifica il processo di generazione delle informazioni e consente di risparmiare tempo e impegno. La procedura permette di condividere un dominio e la relativa Knowledge Base con altri utenti.  
  
 È possibile esportare un dominio singolo o composito. Un file DQS contenente un singolo dominio include tutti i dati del dominio stesso tra cui le proprietà, i valori e le regole, tranne le informazioni sui dati di riferimento collegati. Un file DQS che contiene un dominio composito include tutti i dati di tale dominio, compresi i dati dei domini singoli contenuti al suo interno, nonché le proprietà, le relazioni e le regole del dominio composito stesso, tranne le informazioni sui dati di riferimento. È necessario collegare il dominio o il dominio composito nuovamente ai servizi dati di riferimento appropriati, se necessario, dopo avere importato il file DQS. Vengono esportati sia i dati pubblicati che quelli non pubblicati.  
  
 Il file di dati DQS creato dal processo di esportazione viene crittografato, pertanto non è possibile visualizzarne i contenuti.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Per esportare un dominio in un file di dati DQS, è necessario avere creato e selezionato un dominio singolo o composito contenente più domini singoli. Non è necessario disporre di un file DQS in cui esportare, in quanto verrà creato automaticamente.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per esportare un dominio in un file DQS è necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN.  
  
##  <a name="Export"></a> Esportazione di un dominio in un file DQS  
 È possibile esportare da qualsiasi pagina Gestione dominio. Il comando di esportazione è disponibile sia da un controllo nell'interfaccia utente che da un comando nel menu di scelta rapida del riquadro Elenco domini.  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Client Data Quality](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] aprire una Knowledge Base nell'attività Gestione dominio.  
  
3.  Nel **pagina Gestione dominio** (con qualsiasi scheda selezionata), selezionare un singolo dominio o un dominio composito di **dominio** elenco.  
  
4.  Fare clic sull'icona **Esporta dati Knowledge Base** sopra l'elenco di domini, quindi fare clic su **Esporta dominio**. In alternativa, è possibile fare doppio clic il dominio di **dominio** elenco, scegliere **esportare**, e quindi fare clic su **Esporta dominio**.  
  
5.  Nel **esportare File di dati** la finestra di dialogo, passare alla cartella che si desidera salvare il file nel nome del file o mantenere il nome predefinito, mantenere **file di dati DQS (\*DQS)** come il **Salva come**, e quindi fare clic su **salvare**.  
  
6.  Nella finestra di dialogo **Esporta dominio** verificare che la riga dello stato indichi che l'esportazione è stata completata. Scegliere **OK**.  
  
##  <a name="FollowUp"></a> Completamento: Dopo avere esportato un dominio in un file DQS  
 Dopo avere esportato un dominio in un file DQS, è possibile importare il dominio in un'altra Knowledge Base.  
  
  