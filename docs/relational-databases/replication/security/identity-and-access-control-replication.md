---
title: Controllo di identità e accesso (replica) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- access controls [SQL Server replication]
- security [SQL Server replication], identity and access control
- authentication [SQL Server replication]
- identity [Replication]
ms.assetid: 4da0e793-1ee4-4f69-a80b-45c6732a238d
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ca8cbf2c68de39fc5f918390246a762955cf48a0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="identity-and-access-control-replication"></a>Controllo di identità e accesso (replica)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'autenticazione è il processo in base al quale un'entità (in genere un computer in questo contesto) verifica l'identità di un'altra entità, detta anche un *principale*, (in genere un altro computer o utente). L'autorizzazione è il processo che consente di concedere a un'entità autenticata l'accesso alle risorse, ad esempio un file nel file system o una tabella in un database.  
  
 La sicurezza della replica si basa sull'autenticazione e sull'autorizzazione per controllare l'accesso agli oggetti di database replicati e ai computer e agli agenti coinvolti nell'elaborazione della replica. Questo processo viene eseguito mediante tre meccanismi:  
  
-   Sicurezza degli agenti  
  
     Il modello di sicurezza degli agenti di replica garantisce un controllo dettagliato sugli account utilizzati per eseguire gli agenti e stabilire connessioni. Per informazioni dettagliate sul modello di sicurezza degli agenti, vedere [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md). Per informazioni sull'impostazione di account di accesso e password per gli agenti, vedere [Gestire gli account di accesso e le password nella replica](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md).  
  
-   Ruoli di amministrazione  
  
     Verificare che vengano utilizzati i ruoli appropriati del server e del database per la configurazione, la manutenzione e l'elaborazione della replica. Per altre informazioni, vedere [Security Role Requirements for Replication](../../../relational-databases/replication/security/security-role-requirements-for-replication.md).  
  
-   Elenco di accesso alla pubblicazione  
  
     Concedere l'accesso alle pubblicazioni tramite l'elenco di accesso alla pubblicazione, che funziona in maniera analoga a un elenco di controllo di accesso [!INCLUDE[msCoName](../../../includes/msconame-md.md)] . Quando un Sottoscrittore si connette al server di pubblicazione o al server di distribuzione e richiede l'accesso a una pubblicazione, le informazioni di autenticazione passate dall'agente vengono controllate in base all'elenco di accesso alla pubblicazione. Per altre informazioni e procedure consigliate relative all'elenco di accesso alla pubblicazione, vedere [Proteggere il server di pubblicazione](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
## <a name="filtering-published-data"></a>Applicazione di filtri ai dati pubblicati  
 Oltre a utilizzare l'autenticazione e l'autorizzazione per controllare l'accesso ai dati e agli oggetti replicati, la replica include due opzioni per controllare quali dati rendere disponibili nel Sottoscrittore: applicazione di filtri a colonne e a righe. Per altre informazioni sui filtri, vedere [Filtrare i dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md).  
  
 Quando si definisce un articolo, è possibile pubblicare solo le colonne necessarie per la pubblicazione e omettere quelle superflue o che contengono dati riservati. Quando ad esempio si pubblica la tabella **Customer** dal database Adventure Works per gli agenti di vendita interessati, è possibile omettere la colonna **AnnualSales** che può essere rilevante solo per i dirigenti dell'azienda.  
  
 L'applicazione di filtri ai dati pubblicati consente di limitare l'accesso ai dati e di specificare i dati da rendere disponibili nel Sottoscrittore. È possibile, ad esempio, filtrare la tabella **Customer** in modo che i partner aziendali ricevano solo le informazioni relative ai clienti per cui nella colonna **ShareInfo** è impostato il valore "yes". Nella replica di tipo merge è necessario tenere in considerazione alcuni aspetti relativi alla sicurezza se si utilizza un filtro con parametri che include HOST_NAME(). Per ulteriori informazioni, vedere la sezione relativa all'utilizzo dei filtri con HOST_NAME() in [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e protezione &#40;replica&#41;](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [Panoramica della sicurezza &#40;replica&#41;](../../../relational-databases/replication/security/security-overview-replication.md)   
 [Attenuazione di minacce e vulnerabilità &#40;replica&#41;](../../../relational-databases/replication/security/threat-and-vulnerability-mitigation-replication.md)  
  
  
