---
title: MSSQLSERVER_17132 | Microsoft Docs
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
- 17132 (Database Engine error)
ms.assetid: d1d198bd-6730-4394-bd5f-28f320c01a38
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 10fcbe092dd11b0a040d81228accf181f6882065
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver17132"></a>MSSQLSERVER_17132
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17132|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|INIT_NODESSPACE|  
|Testo del messaggio|Impossibile avviare il server. Memoria insufficiente per il descrittore. Ridurre il carico di memoria non essenziale o aumentare la memoria del sistema.|  
  
## <a name="explanation"></a>Spiegazione  
Impossibile allocare memoria sufficiente per archiviare il descrittore interno del server.  
  
## <a name="user-action"></a>Azione dell'utente  
Aggiungere una quantità maggiore di memoria al computer. Potrebbe essere utile eseguire alcuni passaggi generici per la risoluzione dei problemi relativi alla memoria.  
  
