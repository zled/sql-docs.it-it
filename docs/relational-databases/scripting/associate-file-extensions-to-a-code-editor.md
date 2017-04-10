---
title: "Associazione di estensioni di file a un editor di codice | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "estensioni di file [SQL Server]"
  - "associazione delle estensioni di file [SQL Server]"
  - "editor di query [SQL Server Management Studio], associazione delle estensioni di file"
ms.assetid: 193630f4-93de-4950-8f36-68702531f925
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Associazione di estensioni di file a un editor di codice
  L'associazione di estensioni di file a un editor di codice specifico consente di aprire un file con l'editor di codice [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] appropriato quando si fa doppio clic su un file in Esplora risorse. L'associazione delle estensioni utilizzate solitamente da [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ad esempio sql e mdx, viene eseguita durante l'installazione. È inoltre necessario associare le nuove estensioni di file a [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] nel file system. Questa caratteristica consente di aprire file creati con altri editor oppure di aprire file rinominati, ad esempio copie di backup di file con estensione sql rinominati con estensione bak.  
  
 Il processo è suddiviso in due passaggi. È innanzitutto necessario associare l'estensione a [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] e quindi associare l'estensione a un editor di codice specifico.  
  
### Per associare una nuova estensione di file a SQL Server Management Studio  
  
1.  Fare clic sul pulsante **Start**, scegliere **Tutti i programmi**, **Accessori** e quindi **Esplora risorse**.  
  
2.  In Esplora risorse scegliere **Opzioni cartella** dal menu **Strumenti**.  
  
3.  Nella finestra di dialogo **Opzioni cartella** fare clic su **Nuovo** nella scheda **Tipi di file**.  
  
4.  Nella finestra di dialogo **Creazione nuova estensione** immettere nella casella **Estensione file** la nuova estensione di file da associare e quindi fare clic su **OK**. Non inserire un punto davanti all'estensione.  
  
5.  Selezionare la nuova estensione nella casella **Tipi di file registrati**, quindi fare clic su **Cambia**.  
  
6.  Nella finestra di dialogo **Apri con** fare clic su **SSMS - SQL Server Management Studio** e quindi su **OK**.  
  
7.  Fare clic su **Chiudi** per chiudere la finestra di dialogo **Opzioni cartella**, quindi chiudere Esplora risorse.  
  
### Per associare una nuova estensione di file a un editor di codice in SQL Server Management Studio  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** fare clic su **Editor di testo** e quindi su **Estensione file**.  
  
3.  Immettere la nuova estensione di file nella casella **Estensione**.  
  
4.  Nella casella **Editor** selezionare l'editor di codice da usare per aprire questo tipo di file, fare clic su **Aggiungi** e quindi su **OK**.  
  
## Vedere anche  
 [Utilità Ssms](../../tools/sql-server-management-studio/ssms-utility.md)  
  
  