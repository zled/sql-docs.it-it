---
title: MSSQLSERVER_41030 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7f3514eea0d71d55332b4bfbdd4d3ee5fa08c702
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408861"
---
# <a name="mssqlserver41030"></a>MSSQLSERVER_41030
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41030|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|OPEN_CLUSTER_SUB_KEY|  
|Testo del messaggio|Impossibile aprire la sottochiave del Registro di sistema WSFC (Windows Server Failover Clustering) '%.*ls', codice di errore %d.  La chiave padre è la chiave radice cluster.  È possibile che il servizio WSFC non sia in esecuzione o non sia accessibile nello stato corrente o che gli argomenti specificati non siano validi. Se il gruppo di disponibilità corrispondente è stato eliminato, l'errore è previsto. Per informazioni su questo codice di errore, vedere la sezione relativa ai codici di errore di sistema nella documentazione sullo sviluppo per Windows.|  
  
## <a name="explanation"></a>Spiegazione  
 Se un cluster WSFC viene eliminato, vengono rimosse tutte le chiavi del Registro di sistema correlate a [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
## <a name="user-action"></a>Azione dell'utente  
 Dopo aver creato di nuovo il cluster WSFC, disabilitare e quindi riabilitare AlwaysOn in ogni nodo del cluster in cui un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è abilitata per AlwaysOn. Per questa attività è possibile utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitare e disabilitare gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)   
 [Windows Server Failover Clustering &#40;WSFC&#41; con SQL Server](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
