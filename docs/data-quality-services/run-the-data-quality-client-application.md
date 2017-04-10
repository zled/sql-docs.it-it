---
title: "Eseguire l&#39;applicazione client Data Quality | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.browseforservers.f1"
  - "sql13.dqs.connecttoserver.f1"
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# Eseguire l&#39;applicazione client Data Quality
  Eseguire [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], e accedere a un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 È necessario aver completato l'installazione di [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] tramite l'esecuzione del file DQSInstaller.exe. Per ulteriori informazioni, vedere [DQSInstaller.exe eseguire per completare l'installazione Server qualità dati](../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per potere accedere al [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], è necessario disporre di uno dei tre ruoli DQS (dqs_adminstrator, dqs_kb_editor o dqs_kb_operator) concessi per il database DQS_MAIN.  
  
##  <a name="Run"></a> Eseguire il client Data Quality  
 Per eseguire [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] nel computer in cui è installato:  
  
1.  Fare clic su **avviare**, scegliere **tutti i programmi**, fare clic su **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, fare clic su **Data Quality Services**, quindi fare clic su **Client Data Quality**.  
  
2.  Nel **Connetti al Server** la finestra di dialogo:  
  
    1.  Specificare il server a cui si desidera connettere l'applicazione [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Selezionare **(LOCAL)** a cui connettersi [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] nel computer locale. È inoltre possibile fare clic sulla freccia rivolta verso il basso e selezionare **\< ulteriori server nella rete Sfoglia>** per connettersi a un altro server (o per connettersi al server locale in base al nome). Il **Cerca server** verrà visualizzata la finestra di dialogo. È possibile selezionare un server di **server locali** scheda o nel **server della rete** scheda.  
  
    2.  Per crittografare trasferimento dei dati tra [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] e [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], fare clic su **Opzioni**, quindi selezionare il **Encrypt Connection** casella di controllo.  
  
3.  Fare clic su **Connetti**.  
  
 Verrà visualizzata la schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Per ulteriori informazioni, vedere [schermata Data Quality Client Home](../data-quality-services/data-quality-client-home-screen.md).  
  
  