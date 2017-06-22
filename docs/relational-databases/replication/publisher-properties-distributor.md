---
title: "Proprietà server di pubblicazione - Database di distribuzione | Microsoft Docs"
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
- sql13.rep.configdistwizard.distpubproperties.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: ab6ada76-0f99-43fe-b524-baac7b1bc483
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a0fbae64d400b0e4b1b55a5f4495e242b631a7ab
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="publisher-properties---distributor"></a>Proprietà server di pubblicazione - Server di distribuzione
  La finestra di dialogo **Proprietà server di pubblicazione** consente di visualizzare e modificare le proprietà associate alla relazione tra il server di pubblicazione e il relativo server di distribuzione.  
  
## <a name="options"></a>Opzioni  
 **Connessione agente al server di pubblicazione**  
 Consente di specificare il contesto in cui gli agenti indicati di seguito creeranno connessioni dal server di distribuzione al server di pubblicazione:  
  
-   Agente di lettura coda per pubblicazioni transazionali che consentono sottoscrizioni ad aggiornamento in coda.  
  
-   Agente snapshot e agente di lettura log per pubblicazioni Oracle.  
  
 Selezionare **Rappresenta l'account del processo dell'agente** per stabilire una connessione al server di pubblicazione tramite il contesto dell'account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows con cui vengono eseguiti gli agenti oppure specificare **Autenticazione di SQL Server**e quindi immettere un valore per **Nome account di accesso** e **Password**. È consigliabile scegliere l'opzione **Rappresenta l'account del processo dell'agente**. Per altre informazioni sulla sicurezza dell'agente, vedere [Modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 Gli account di Windows con cui vengono eseguiti questi agenti sono specificati nella Creazione guidata nuova pubblicazione. È possibile modificare gli account seguenti:  
  
-   Nella finestra di dialogo **Proprietà server di distribuzione** per l'agente di lettura coda.  
  
-   Nella finestra di dialogo **Proprietà server di pubblicazione** per gli agenti snapshot e di lettura log.  
  
 **Varie**  
 Le proprietà **Tipo server di pubblicazione** e **Nome database di distribuzione** sono di sola lettura. La proprietà **Cartella snapshot predefinita** può essere modificata. Per altre informazioni sulla cartella snapshot, vedere [Proteggere la cartella snapshot](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Riferimento alle proprietà &#40;replica&#41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  
