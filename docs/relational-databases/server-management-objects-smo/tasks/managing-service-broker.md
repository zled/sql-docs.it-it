---
title: Gestione di Service Broker | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Service Broker [SMO]
ms.assetid: b29d7432-d1e5-4bb6-b544-57b3a9430f95
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c95f140f023d59e07161ac0f8841d306425b77c7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="managing-service-broker"></a>Gestione di Service Broker
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]In SMO la [!INCLUDE[ssSB](../../../includes/sssb-md.md)] oggetti vengono individuati nel **Microsoft.SqlServer.Management.Smo.Broker** spazio dei nomi, che richiede un riferimento a Microsoft.SqlServer.Smo.dll. Un riferimento a Microsoft.SqlServer.ServiceBrokerEnum.dll è richiesto anche per supportare informazioni sulle classi.  
  
 SMO fornisce un set di oggetti [!INCLUDE[ssSB](../../../includes/sssb-md.md)] che permettono la gestione a livello di programmazione (DDL) dell'implementazione di [!INCLUDE[ssSB](../../../includes/sssb-md.md)], inclusa la definizione di tipi di messaggio, contratti, code e servizi. Poiché SMO è un strumento di gestione che non è destinato alla modifica dei dati, l'invio e la ricezione di messaggi [!INCLUDE[ssSB](../../../includes/sssb-md.md)] non sono supportati in SMO.  
  
 In SMO l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> è la classe di livello principale all'interno della quale si trovano tutte le funzionalità di [!INCLUDE[ssSB](../../../includes/sssb-md.md)]. Un'implementazione di [!INCLUDE[ssSB](../../../includes/sssb-md.md)] è necessaria per ogni database interessato dall'applicazione di messaggistica distribuita. L'oggetto <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker>, pertanto, è un elemento figlio dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Database>.  
  
 L'oggetto <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> contiene raccolte degli oggetti seguenti, utilizzati per definire l'implementazione di [!INCLUDE[ssSB](../../../includes/sssb-md.md)]:  
  
-   Gli oggetti <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> rappresentano tipi di messaggio che definiscono il contenuto dei messaggi.  
  
-   Gli oggetti <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> rappresentano contratti che specificano la direzione e il tipo dei messaggi in una determinata conversazione.  
  
-   Gli oggetti <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> archiviano messaggi prima dell'invio e dopo la ricezione. Tali oggetti consentono la comunicazione asincrona tra servizi, nonché altri vantaggi, ad esempio il blocco automatico dei messaggi nello stesso gruppo di conversazioni.  
  
-   Gli oggetti <xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> rappresentano i servizi di [!INCLUDE[ssSB](../../../includes/sssb-md.md)], che sono endpoint indirizzabili per le conversazioni. I messaggi [!INCLUDE[ssSB](../../../includes/sssb-md.md)] vengono inviati da un servizio a un altro servizio. Un servizio specifica una coda contenente messaggi e i contratti per cui il servizio può fungere da destinazione.  
  
-   Gli oggetti <xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> rappresentano le impostazioni utilizzate da [!INCLUDE[ssSB](../../../includes/sssb-md.md)] per la sicurezza e l'autenticazione quando si comunica con un servizio remoto.  
  
-   Gli oggetti <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> rappresentano una route [!INCLUDE[ssSB](../../../includes/sssb-md.md)] che contiene le informazioni sul percorso per il servizio e il database in cui è definito. Una route è necessaria per il recapito dei messaggi. Per impostazione predefinita, ogni database contiene una route che specifica il percorso come istanza corrente di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>   
 [SQL Server Service Broker](../../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
