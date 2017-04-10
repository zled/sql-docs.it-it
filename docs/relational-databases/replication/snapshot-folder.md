---
title: "Cartella snapshot | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.replicationutilities.specifysnapshotfolder.f1"
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# Cartella snapshot
  Il **cartella Snapshot** pagina viene visualizzata nella configurazione guidata distribuzione e la creazione guidata nuova pubblicazione. Il percorso specificato per la cartella snapshot verrà utilizzata come il valore predefinito per tutti i server di pubblicazione abilitato in questa procedura guidata (nella cartella snapshot predefinita non è applicabile ai server di pubblicazione abilitati successivamente tramite la **proprietà server di distribuzione** la finestra di dialogo). È possibile eseguire l'override di questa impostazione predefinita per qualsiasi server di pubblicazione sul **editori** pagina della configurazione guidata distribuzione o **proprietà server di distribuzione** la finestra di dialogo.  
  
 La cartella snapshot è semplicemente una directory designata come condivisione. Gli agenti che eseguono letture e scritture in questa cartella devono disporre di autorizzazioni sufficienti per accedervi. Per ulteriori informazioni sulla protezione della cartella in modo appropriato, vedere [sicurezza della cartella Snapshot](../../relational-databases/replication/security/secure-the-snapshot-folder.md). Prima di implementare la replica è necessario verificare che gli agenti di replica possano connettersi alla cartella snapshot. Accedere con l'account che verrà utilizzato da ogni agente e quindi tentare di accedere alla cartella snapshot.  
  
## Opzioni  
 **Cartella snapshot**  
 Consente di immettere il percorso della cartella in cui archiviare i file di snapshot.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] È consigliabile utilizzare una condivisione di rete come percorso della cartella snapshot. I percorsi locali (quelli che iniziano con una lettera di unità, ad esempio c:\\) non sono accessibili per gli agenti su altri computer.  
  
## Vedere anche  
 [Posizioni alternative della cartella snapshot](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Configurazione della distribuzione](../../relational-databases/replication/configure-distribution.md)   
 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  