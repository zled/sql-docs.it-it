---
title: "Proprietà server di pubblicazione - Server di pubblicazione, Database di pubblicazione | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
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
f1_keywords:
- sql13.rep.configdistwizard.pubproperties.pubdb.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5aff4539da6d3b05dc5104c4bc5ce88ebdc6acc4
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="publisher-properties---publisher-publication-databases"></a>Proprietà server di pubblicazione - Server di pubblicazione, Database di pubblicazione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La pagina **Database di pubblicazione** della finestra di dialogo **Proprietà server di pubblicazione** consente a un utente membro del ruolo predefinito del server **sysadmin** di abilitare i database per la replica. L'abilitazione di un database non ne implica la sua pubblicazione, ma consente a qualsiasi utente membro del ruolo predefinito del database **db_owner** per tale database di creare una o più pubblicazioni sul database.  
  
## <a name="options"></a>Opzioni  
 **Transazionale**  
 Selezionare questa casella di controllo per consentire agli utenti membri del ruolo predefinito del database **db_owner** di creare pubblicazioni snapshot o pubblicazioni transazionali nel database.  
  
 **Merge**  
 Selezionare questa casella di controllo per consentire agli utenti membri del ruolo predefinito del database **db_owner** di creare pubblicazioni di tipo merge nel database.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Riferimento alle proprietà &#40;replica&#41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  
