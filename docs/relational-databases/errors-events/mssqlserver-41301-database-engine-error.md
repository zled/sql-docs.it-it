---
title: MSSQLSERVER_41301 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 38647b63d1b67e7998e6962e4939b9ddd45ef87c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver41301"></a>MSSQLSERVER_41301
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41301|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|COMMIT_DEPENDENCY_FAILURE|  
|Testo del messaggio|Una transazione precedente da cui dipende la transazione corrente è stata interrotta. Impossibile eseguire il commit della transazione corrente.|  
  
## <a name="explanation"></a>Spiegazione  
La transazione ha rilevato un errore di dipendenza ed è stata eliminata.  
  
Questo errore può essere causato anche da troppe transazioni dipendenti. Qualsiasi transazione di scrittura può presentare un numero limitato di transazioni dipendenti. Ad esempio, questo errore si può verificare se tramite troppe transazioni di lettura si tenta di accettare una dipendenza dalla transazione di aggiornamento.  
  
## <a name="user-action"></a>Azione dell'utente  
Non eseguire operazioni sulla transazione. Chiamare ROLLBACK TRAN per eseguire il rollback della transazione. Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Vedere anche  
[Abilitare e disabilitare la funzionalità Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](~/database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
