---
title: "Proprietà pubblicazione, Snapshot FTP e Internet | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.internetsynchronization.f1
ms.assetid: 8e0198c3-5e4e-418c-9920-78ccbbfc1323
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: c0e55c0e35039490f0ce4cd8a7fb6d7e232c05aa
ms.openlocfilehash: 3458af05f6289366c7a9391016327ff9d11c1434
ms.contentlocale: it-it
ms.lasthandoff: 04/15/2017

---
# <a name="publication-properties-ftp-snapshot-and-internet"></a>Proprietà pubblicazione, Snapshot FTP e Internet
  Questa pagina consente di:  
  
-   Impostare le proprietà per il recapito dello snapshot tramite FTP (File Transfer Protocol). Per altre informazioni, vedere [Trasferire snapshot tramite FTP](../../relational-databases/replication/transfer-snapshots-through-ftp.md). Per eseguire il recapito di snapshot tramite FTP è necessario configurare un server FTP. Per ulteriori informazioni, vedere la documentazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
    > [!NOTE]  
    >  Le modifiche apportate a qualsiasi impostazione relativa al protocollo FTP richiedono la generazione di un nuovo snapshot.  
  
-   Impostare le proprietà per la sincronizzazione Web per la replica di tipo merge in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive, in modo da consentire la sincronizzazione delle sottoscrizioni tramite il protocollo HTTPS. Per utilizzare la sincronizzazione Web è necessario configurare un server [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS). Per altre informazioni, vedere [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
## <a name="options"></a>Opzioni  
 **Accedi ai file di snapshot tramite FTP**  
 Selezionare **I Sottoscrittori possono scaricare i file di snapshot utilizzando FTP (File Transfer Protocol)**e specificare **Nome server FTP**, **Numero di porta**, **Percorso dalla cartella radice FTP**, **Account di accesso**e **Password**per consentire ai Sottoscrittori l'utilizzo del protocollo FTP per il recapito di snapshot.  
  
 La selezione di questa opzione consente ai Sottoscrittori di utilizzare il protocollo FTP per recuperare i file di snapshot, senza tuttavia imporne l'obbligo di utilizzo. Se si seleziona questa opzione, l'impostazione predefinita per la Creazione guidata nuova sottoscrizione viene impostata per consentire al Sottoscrittore di recuperare file di snapshot tramite FTP. Per modificare l'impostazione utilizzare la finestra di dialogo **Proprietà sottoscrizione** . Se si consente ai Sottoscrittori l'accesso ai file di snapshot tramite FTP, specificare la cartella FTP come posizione per i file di snapshot nella pagina **Snapshot** della finestra di dialogo **Proprietà pubblicazione** . In tal modo l'agente snapshot aggiornerà automaticamente i file nella cartella FTP quando viene generato un nuovo snapshot. Se la posizione non è impostata sulla cartella FTP, sarà necessario aggiornare i file manualmente ogni volta che vengono generati nuovi snapshot. Per altre informazioni, vedere [Recapitare uno snapshot tramite FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
 **Sincronizzazione Web**  
 Solo per la replica di tipo merge. Selezionare **I Sottoscrittori possono eseguire la sincronizzazione tramite connessione a un server Web**e specificare l'indirizzo di un server Web per consentire ai Sottoscrittori della replica di tipo merge di utilizzare la sincronizzazione Web. Il server Web è necessario utilizzare Secure Sockets Layer (SSL) e l'indirizzo Web deve essere completo, ad esempio `https://server.domain.com/synchronize`. Per altre informazioni, vedere [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzare e modificare le proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni pull](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni push](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Creare e applicare lo snapshot iniziale](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Pubblicare dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
