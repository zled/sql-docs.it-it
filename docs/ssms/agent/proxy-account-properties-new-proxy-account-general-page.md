---
title: Proprietà account proxy - Nuovo account proxy (pagina Generale) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ag.proxy.general.f1
ms.assetid: 5cd81265-bf59-413b-8397-150ddc70d0c7
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bfe2ff4e8cc614386634a2b80afcee82df2dcf18
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="proxy-account-properties---new-proxy-account-general-page"></a>Proprietà del proxy - Nuovo account proxy (pagina Generale)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Usare questa pagina per visualizzare o modificare le proprietà di un account proxy di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
**Nome proxy**  
Consente di digitare il nome del proxy.  
  
**Nome credenziali**  
Consente di digitare il nome delle credenziali per il proxy.  
  
> [!NOTE]  
> Il nome delle credenziali fornito deve essere il nome di credenziali esistenti. Per informazioni sulla creazione di credenziali, vedere [Procedura: Creazione di un Proxy (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/c1e77e91-2a69-40d9-b8b3-97cffc710586)  
  
**...**  
Apre la finestra di dialogo **Seleziona credenziali** .  
  
**Descrizione**  
Consente di digitare la descrizione per il proxy.  
  
**Attivo nei sottosistemi seguenti**  
Consente di selezionare i sottosistemi ai quali ha accesso l'account proxy.  
  
**Riassegna i passaggi del processo a**  
Consente di selezionare il proxy al quale riassegnare i passaggi del processo. Questo elenco è abilitato quando si revoca l'accesso a un sottosistema al quale il proxy aveva accesso in precedenza.  
  
## <a name="see-also"></a>Vedere anche  
[Creazione di un proxy di SQL Server Agent](../../ssms/agent/create-a-sql-server-agent-proxy.md)  
  
