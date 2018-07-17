---
title: Proprietà pubblicazione (pagina Sicurezza agente) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.agentsecurity.f1
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c4b3c16d6baad3acd6fe3e9c2ff5c9b9e6d6fd16
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37352023"
---
# <a name="publication-properties-agent-security"></a>Proprietà pubblicazione (pagina sicurezza agente)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La pagina **Sicurezza agente** della finestra di dialogo **Proprietà pubblicazione** consente di accedere alle impostazioni relative agli account nell'ambito dei quali gli agenti seguenti vengono eseguiti e si connettono ai computer inclusi in una topologia di replica.  
  
-   Agente snapshot per tutte le pubblicazioni.  
  
-   Agente di lettura log per tutte le pubblicazioni transazionali. Per ogni database pubblicato per la replica transazionale, esiste un solo agente di lettura log. Le modifiche apportate alle impostazioni dell'agente di lettura log sono valide per tutte le pubblicazioni transazionali in un database.  
  
-   Agente di lettura coda per pubblicazioni transazionali che consentono sottoscrizioni ad aggiornamento in coda. A ogni database di distribuzione è associato un agente di lettura coda. Le modifiche apportate all'agente di lettura coda sono valide per tutte le pubblicazioni transazionali con sottoscrizioni ad aggiornamento in coda che utilizzano il medesimo database di distribuzione. Per altre informazioni sulle impostazioni di sicurezza di Agente di lettura coda, vedere [Visualizzare e modificare le impostazioni di sicurezza della replica](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Per ulteriori informazioni sulle autorizzazioni e le impostazioni di sicurezza necessarie per ogni agente, vedere [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="options"></a>Opzioni  
 **Impostazioni di sicurezza** o **Crea agente**  
 Se è stato creato un processo agente, fare clic su **Impostazioni di sicurezza** per accedere a una finestra di dialogo che consente di modificare le impostazioni di sicurezza relative a un agente. Se non è stato creato alcun processo agente, fare clic su **Crea agente** per crearne uno e specificare le relative impostazioni di sicurezza.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzare e modificare le proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Pubblicare dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione #40;replica&#41;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
