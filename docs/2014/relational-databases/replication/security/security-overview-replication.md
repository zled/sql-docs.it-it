---
title: Panoramica della sicurezza (replica) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- authorization [SQL Server replication]
- cryptography [SQL Server replication]
- encryption [SQL Server replication]
- security [SQL Server replication], about security
- authentication [SQL Server replication]
ms.assetid: 27828fe4-3b54-4c33-886e-08e8279e34b5
caps.latest.revision: 44
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 62567dbbb53db61780f002779abb825e19287578
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148262"
---
# <a name="security-overview-replication"></a>Panoramica della sicurezza (replica)
  La modalità di protezione dell'ambiente di replica dipende essenzialmente dalla comprensione delle opzioni di autenticazione e autorizzazione, dell'utilizzo corretto delle funzionalità di filtro della replica e delle misure specifiche per la protezione di ogni componente dell'ambiente di replica. L'ambiente di replica include il server di distribuzione, il server di pubblicazione, i Sottoscrittori e la cartella snapshot. In questo capitolo vengono fornite informazioni sulla sicurezza della replica, la quale è basata sulla sicurezza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e di Windows. È pertanto necessario conoscere questi ambiti di base e le specifiche della sicurezza della replica. Per altre informazioni, vedere [Considerazioni sulla sicurezza per un'installazione di SQL Server](../../../sql-server/install/security-considerations-for-a-sql-server-installation.md). Per ulteriori informazioni sulla sicurezza per la pubblicazione Oracle, vedere la sezione relativa al modello di sicurezza della replica nell'argomento [Design Considerations and Limitations for Oracle Publishers](../non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Attenuazione di minacce e vulnerabilità &#40;replica&#41;](threat-and-vulnerability-mitigation-replication.md)  
 Illustra le potenziali minacce per una topologia di replica e descrive come ridurre i rischi connessi.  
  
 [Controllo di identità e accesso &#40;replica&#41;](identity-and-access-control-replication.md)  
 Descrive come utilizzare l'autenticazione, l'autorizzazione e i filtri per proteggere una topologia di replica.  
  
 [Sviluppo sicuro &#40;replica&#41;](secure-development-replication.md)  
 Descrive il comportamento della sicurezza della replica, le procedure consigliate per la sicurezza della replica e le autorizzazioni minime per la replica.  
  
 [Distribuzione sicura &#40;replica&#41;](secure-deployment-replication.md)  
 Descrive come ottimizzare la protezione di tutti i componenti di una topologia di replica.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e protezione #40;replica&#41;](security-and-protection-replication.md)  
  
  
