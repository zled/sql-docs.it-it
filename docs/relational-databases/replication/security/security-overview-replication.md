---
title: Panoramica della sicurezza (replica) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [SQL Server replication]
- cryptography [SQL Server replication]
- encryption [SQL Server replication]
- security [SQL Server replication], about security
- authentication [SQL Server replication]
ms.assetid: 27828fe4-3b54-4c33-886e-08e8279e34b5
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6aeaff943dfd5a20c7e8cd68424a0294b7e694b7
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="security-overview-replication"></a>Panoramica della sicurezza (replica)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La modalità di protezione dell'ambiente di replica dipende essenzialmente dalla comprensione delle opzioni di autenticazione e autorizzazione, dell'utilizzo corretto delle funzionalità di filtro della replica e delle misure specifiche per la protezione di ogni componente dell'ambiente di replica. L'ambiente di replica include il server di distribuzione, il server di pubblicazione, i Sottoscrittori e la cartella snapshot. In questo capitolo vengono fornite informazioni sulla sicurezza della replica, la quale è basata sulla sicurezza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e di Windows. È pertanto necessario conoscere questi ambiti di base e le specifiche della sicurezza della replica. Per altre informazioni, vedere [Considerazioni sulla sicurezza per un'installazione di SQL Server](../../../sql-server/install/security-considerations-for-a-sql-server-installation.md). Per ulteriori informazioni sulla sicurezza per la pubblicazione Oracle, vedere la sezione relativa al modello di sicurezza della replica nell'argomento [Design Considerations and Limitations for Oracle Publishers](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Attenuazione di minacce e vulnerabilità &#40;replica&#41;](../../../relational-databases/replication/security/threat-and-vulnerability-mitigation-replication.md)  
 Illustra le potenziali minacce per una topologia di replica e descrive come ridurre i rischi connessi.  
  
 [Controllo di identità e accesso &#40;replica&#41;](../../../relational-databases/replication/security/identity-and-access-control-replication.md)  
 Descrive come utilizzare l'autenticazione, l'autorizzazione e i filtri per proteggere una topologia di replica.  
  
 [Sviluppo sicuro &#40;replica&#41;](../../../relational-databases/replication/security/secure-development-replication.md)  
 Descrive il comportamento della sicurezza della replica, le procedure consigliate per la sicurezza della replica e le autorizzazioni minime per la replica.  
  
 [Distribuzione sicura &#40;replica&#41;](../../../relational-databases/replication/security/secure-deployment-replication.md)  
 Descrive come ottimizzare la protezione di tutti i componenti di una topologia di replica.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e protezione #40;replica&#41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
