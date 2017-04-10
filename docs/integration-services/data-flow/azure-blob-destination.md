---
title: "Destinazione BLOB di Azure | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afpblobdest.f1"
  - "sql14.dts.designer.afpblobdest.f1"
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
caps.latest.revision: 12
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Destinazione BLOB di Azure
  Il componente **Destinazione BLOB di Azure** consente a un pacchetto SSIS di scrivere dati in un BLOB di Azure. I formati di file supportati sono CSV e AVRO. 
  
>   [!NOTE] Per assicurarsi che Gestione della connessione di archiviazione di Azure e i componenti da cui è usato, ossia l'origine BLOB, la destinazione BLOB e le attività di caricamento e download di BLOB, riescano a connettersi a entrambi gli account di archiviazione generici e agli account di archiviazione BLOB, scaricare [qui](https://www.microsoft.com/download/details.aspx?id=49492) la versione più recente del Feature Pack di Azure. Per altre informazioni su questi due tipi di account di archiviazione, vedere [Introduzione ad Archiviazione di Microsoft Azure](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts).
  
 Trascinare **Destinazione BLOB di Azure** nella finestra di progettazione del flusso di dati e fare doppio clic per visualizzare l'editor.  
  
 **Destinazione BLOB di Azure** è un componente del Feature Pack di SQL Server Integration Services (SSIS) per Azure per SQL Server 2016. Scaricare il Feature Pack [qui](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
1.  Nel campo **Gestione connessione di archiviazione di Azure** specificare un'istanza esistente di Gestione connessioni dell'archiviazione di Azure o creare una nuova istanza che fa riferimento a un account di archiviazione di Azure.  
  
2.  Nel campo **Nome contenitore BLOB** specificare il nome del contenitore BLOB che contiene i file di origine.  
  
3.  Nel campo **Nome BLOB** specificare il percorso per il BLOB.  
  
4.  Nel campo **Formato del file BLOB** specificare il formato BLOB che si vuole usare.  
  
5.  Se il formato del file è CSV, è necessario impostare il valore **Carattere delimitatore di colonna** . Selezionare anche **Nomi di colonne nella prima riga di dati** se la prima riga nel file contiene i nomi di colonna.  
  
6.  Dopo aver specificato le informazioni di connessione, passare alla pagina **Colonne** per eseguire il mapping delle colonne di origine alle colonne di destinazione per il flusso di dati SSIS.  
  
  