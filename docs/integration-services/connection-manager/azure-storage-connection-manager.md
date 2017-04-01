---
title: "Gestione connessione dell&#39;archiviazione di Azure | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afpstorageconn.f1"
  - "sql14.dts.designer.afpstorageconn.f1"
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
caps.latest.revision: 13
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Gestione connessione dell&#39;archiviazione di Azure
  Il componente **Gestione connessione dell'archiviazione di Azure** consente di connettere un pacchetto SSIS a un account di archiviazione di Azure usando i valori specificati per le proprietà: Nome dell'account di archiviazione e Chiave dell'account.  
  
>   [!NOTE] Per assicurarsi che Gestione della connessione di archiviazione di Azure e i componenti da cui è usato, ossia l'origine BLOB, la destinazione BLOB e le attività di caricamento e download di BLOB, riesca a connettersi a entrambi gli account di archiviazione generici e agli account di archiviazione BLOB, scaricare [qui](https://www.microsoft.com/download/details.aspx?id=49492) la versione più recente del Feature Pack di Azure. Per altre informazioni su questi due tipi di account di archiviazione, vedere [Introduzione ad Archiviazione di Microsoft Azure](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts).
  
 **Gestione connessione dell'archiviazione di Azure** è un componente del Feature Pack di SQL Server Integration Services (SSIS) per Azure per SQL Server 2016. Scaricare il Feature Pack [qui](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
1.  Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **Sottoscrizione di Azure**, quindi fare clic su **Aggiungi**.  
  
2.  Nella finestra di dialogo Editor gestione connessione di archiviazione di Azure, scegliere **Usa account Azure** per connettersi a un servizio di archiviazione di Azure con Internet o scegliere **Usa account per sviluppatore locale** per connettersi al servizio locale ospitato dall'emulatore di archiviazione di Azure.  
  
3.  Se si seleziona l'opzione **Usa account Azure** , eseguire queste operazioni:  
  
    1.  Specificare i valori per i campi **Nome dell'account di archiviazione** e **Chiave dell'account** . Questi valori vengono archiviati come dati sensibili nel pacchetto SSIS.  
  
    2.  Selezionare **Usa HTTPS** per usare HTTPS anziché HTTP per connettersi al servizio di archiviazione di Azure.  
  
4.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
5.  È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .  
  
  