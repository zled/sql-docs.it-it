---
title: Trasferire snapshot tramite FTP | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], FTP snapshots
- FTP snapshots [SQL Server replication]
- snapshot replication [SQL Server], FTP
ms.assetid: 55c30791-cd2a-420b-8ba7-5700e005cb45
caps.latest.revision: "40"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4389eb11fae4e538b0f5ff5d98450738b6847ccd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="transfer-snapshots-through-ftp"></a>Trasferimento di snapshot tramite FTP
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Per impostazione predefinita, gli snapshot vengono archiviati in cartelle definite condivisioni UNC. La replica consente inoltre di specificare una condivisione FTP anziché una condivisione UNC. Per utilizzare l'FTP, è necessario configurare un server FTP e quindi configurare una pubblicazione e una o più sottoscrizioni che utilizzeranno l'FTP. Per informazioni sulla configurazione di un server FTP, vedere la documentazione di Internet Information Services (IIS). Se si specificano le informazioni FTP per una pubblicazione, le sottoscrizioni a quella pubblicazione per impostazione predefinita utilizzano l'FTP. FTP viene utilizzato con la sincronizzazione Web solo quando il computer con IIS è separato dal server di distribuzione da un firewall. In questo caso, è possibile utilizzare FTP per trasferire lo snapshot dal server di distribuzione e dal computer che esegue IIS. Per il trasferimento degli snapshot al Sottoscrittore viene sempre utilizzato HTTPS.  
  
> [!IMPORTANT]  
>  È consigliabile utilizzare l'autenticazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows e una condivisione UNC, anziché una condivisione FTP, perché le password FTP devono essere archiviate e la password viene inviata al server FTP come testo normale dal Sottoscrittore o dal computer con IIS che utilizza la sincronizzazione Web. Inoltre, dato che un unico account controlla l'accesso alla condivisione snapshot, non è possibile garantire che un Sottoscrittore di una pubblicazione filtrata di tipo merge abbia accesso solo ai file snapshot della relativa partizione di dati.  
  
 Per recapitare uno snapshot tramite FTP, vedere [Deliver a Snapshot Through FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sincronizzazione Web per la replica di tipo merge](../../relational-databases/replication/web-synchronization-for-merge-replication.md)   
 [Inizializzare una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Opzioni per gli snapshot](../../relational-databases/replication/snapshot-options.md)  
  
  
