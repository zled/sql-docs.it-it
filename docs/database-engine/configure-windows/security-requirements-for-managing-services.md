---
title: Requisiti di sicurezza per la gestione dei servizi | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent service, security
- services [SQL Server], security
- SQL Server services, security
- WMI Providers [SQL Server]
- server configuration [SQL Server]
- security [SQL Server], services
- services [SQL Server], WMI
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cf5902f634cb69689388cadf26c0c53fed607519
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="security-requirements-for-managing-services"></a>Requisiti di sicurezza per la gestione dei servizi
  Per gestire i servizi [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, usare Gestione configurazione SQL Server o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Gestire i servizi su server del cluster tramite Amministrazione cluster.  
  
 Per gestire il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e impostare le opzioni di configurazione del server, è necessario essere membri del ruolo predefinito del server **serveradmin** o **sysadmin** . I membri del gruppo **Administrators** di Windows possono avviare e arrestare i servizi e configurare le opzioni server disponibili in Windows.  
  
> [!NOTE]  
>  Per un corretto funzionamento, è necessario che gli account utilizzati per i servizi siano configurati con dominio, file system e autorizzazioni per il Registro di sistema appropriati. Per informazioni sulle autorizzazioni necessarie, vedere [Configurare account di servizio e autorizzazioni di Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## <a name="windows-management-instrumentation"></a>Strumentazione gestione Windows (WMI)  
 Per visualizzare e modificare alcune delle proprietà del server in Gestione configurazione SQL Server e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] viene utilizzato il servizio Strumentazione gestione Windows (WMI). Per gestire i servizi e ottenere informazioni sullo stato dei servizi, è necessario che l'utente sia autorizzato ad accedere all'oggetto WMI. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]WMI viene utilizzato dalle proprietà del server seguenti:  
  
-   Avvio automatico servizi  
  
-   Parametri di avvio  
  
-   Sicurezza  
  
-   Impostazioni varie  
  
## <a name="related-tasks"></a>Attività correlate  
 [Configurazione di WMI per mostrare lo stato del server in Strumenti SQL Server](http://msdn.microsoft.com/library/7e97197b-ed4d-40d1-9a52-9ab1d92401d7)  
  
## <a name="related-content"></a>Contenuto correlato  
 [Concetti relativi al provider WMI per Gestione configurazione](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  

