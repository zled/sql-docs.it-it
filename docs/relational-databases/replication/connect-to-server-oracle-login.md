---
title: Connetti al server (Oracle), Account di accesso| Microsoft Docs
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
f1_keywords: sql13.rep.oracleconnection.login.f1
helpviewer_keywords: Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 690f1d00b2521231d22d8a0e7ebf5af4ca499bce
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="connect-to-server-oracle-login"></a>Connetti al server (Oracle), Account di accesso
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Usare la scheda **Account di accesso** della finestra di dialogo **Connetti al server** per specificare l'account con cui vengono stabilite le connessioni dal server di distribuzione [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al server di pubblicazione Oracle. È necessario utilizzare lo stesso account specificato per lo schema utente di amministrazione della replica durante la configurazione del server di pubblicazione. Per altre informazioni, vedere [Configurare un server di pubblicazione Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Opzioni  
 **Istanza del server**  
 Transparent Network Substrate del server di pubblicazione Oracle specificato durante la configurazione del software client Oracle installato nel server di distribuzione.  
  
 **Autenticazione**  
 Consente di selezionare l' **Autenticazione standard Oracle** (scelta consigliata) oppure l' **Autenticazione di Windows**. Se si seleziona l' **Autenticazione di Windows**:  
  
-   Il server Oracle deve essere configurato in modo da consentire le connessioni con le credenziali di Windows. Per ulteriori informazioni, vedere la documentazione di Oracle.  
  
-   È necessario eseguire l'accesso con lo stesso account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows specificato per lo schema utente di amministrazione della replica.  
  
 **Account di accesso** e **Password**  
 Se è stata selezionata l' **Autenticazione standard Oracle** per l'opzione **Autenticazione** , specificare l'account di accesso e la password da utilizzare, che devono corrispondere all'account di accesso e alla password specificati per lo schema utente di amministrazione della replica.  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario dei termini per la pubblicazione Oracle](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
