---
title: "Propriet&#224; pubblicazione, Snapshot FTP e Internet | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.internetsynchronization.f1"
ms.assetid: 8e0198c3-5e4e-418c-9920-78ccbbfc1323
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Propriet&#224; pubblicazione, Snapshot FTP e Internet
  Questa pagina consente di:  
  
-   Impostare le proprietà per il recapito dello snapshot tramite FTP (File Transfer Protocol). Per ulteriori informazioni, vedere [trasferire gli snapshot tramite FTP](../../relational-databases/replication/transfer-snapshots-through-ftp.md). Per eseguire il recapito di snapshot tramite FTP è necessario configurare un server FTP. Per ulteriori informazioni, vedere la documentazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
    > [!NOTE]  
    >  Le modifiche apportate a qualsiasi impostazione relativa al protocollo FTP richiedono la generazione di un nuovo snapshot.  
  
-   Impostare le proprietà per la sincronizzazione Web per la replica di tipo merge in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive, in modo da consentire la sincronizzazione delle sottoscrizioni tramite il protocollo HTTPS. Per utilizzare la sincronizzazione Web è necessario configurare un server [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS). Per ulteriori informazioni, vedere [sincronizzazione Web per la replica di tipo Merge](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
## Opzioni  
 **Accedi ai file di snapshot tramite FTP**  
 Selezionare **i sottoscrittori possono scaricare i file di snapshot tramite FTP (File Transfer Protocol)**, e specificare **nome del server FTP**, **il numero di porta**, **percorso dalla cartella radice FTP**, **accesso**, e **Password**, per consentire ai sottoscrittori di utilizzare FTP per il recapito di snapshot.  
  
 La selezione di questa opzione consente ai Sottoscrittori di utilizzare il protocollo FTP per recuperare i file di snapshot, senza tuttavia imporne l'obbligo di utilizzo. Se si seleziona questa opzione, l'impostazione predefinita per la Creazione guidata nuova sottoscrizione viene impostata per consentire al Sottoscrittore di recuperare file di snapshot tramite FTP. Per modificare l'impostazione, utilizzare il **le proprietà della sottoscrizione** la finestra di dialogo. Se si consentono ai sottoscrittori di accedere ai file di snapshot tramite FTP, specificare la cartella FTP come posizione per i file di snapshot nel **Snapshot** pagina la **Proprietà pubblicazione** la finestra di dialogo. In tal modo l'agente snapshot aggiornerà automaticamente i file nella cartella FTP quando viene generato un nuovo snapshot. Se la posizione non è impostata sulla cartella FTP, sarà necessario aggiornare i file manualmente ogni volta che vengono generati nuovi snapshot. Per ulteriori informazioni, vedere [recapitare Snapshot tramite FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
 **Sincronizzazione Web**  
 Solo per la replica di tipo merge. Selezionare **i sottoscrittori possono eseguire la sincronizzazione tramite connessione a un server Web**, e specificare un indirizzo del server Web per consentire ai sottoscrittori di utilizzare la sincronizzazione Web di tipo merge. È necessario che il sito Web utilizzi SSL (Secure Sockets Layer) e che l'indirizzo Web sia completo, ad esempio https://server.domain.com/synchronize. Per altre informazioni, vedere [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Creazione e applicazione dello snapshot iniziale](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  