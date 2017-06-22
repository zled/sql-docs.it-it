---
title: "Proprietà server di pubblicazione - Server di pubblicazione, Database di pubblicazione | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.configdistwizard.pubproperties.pubdb.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cc86424019df085038fffd9b076576eb9c717024
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="publisher-properties---publisher-publication-databases"></a>Proprietà server di pubblicazione - Server di pubblicazione, Database di pubblicazione
  La pagina **Database di pubblicazione** della finestra di dialogo **Proprietà server di pubblicazione** consente a un utente membro del ruolo predefinito del server **sysadmin** di abilitare i database per la replica. L'abilitazione di un database non ne implica la sua pubblicazione, ma consente a qualsiasi utente membro del ruolo predefinito del database **db_owner** per tale database di creare una o più pubblicazioni sul database.  
  
## <a name="options"></a>Opzioni  
 **Transazionale**  
 Selezionare questa casella di controllo per consentire agli utenti membri del ruolo predefinito del database **db_owner** di creare pubblicazioni snapshot o pubblicazioni transazionali nel database.  
  
 **Merge**  
 Selezionare questa casella di controllo per consentire agli utenti membri del ruolo predefinito del database **db_owner** di creare pubblicazioni di tipo merge nel database.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Riferimento alle proprietà &#40;replica&#41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  
