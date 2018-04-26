---
title: MSSQLSERVER_948 | Microsoft Docs
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
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b8cf84fd35ba4555c0be58c5f57960e7d0ae10d6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver948"></a>MSSQLSERVER_948
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|948|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|ND|  
|Testo del messaggio|Impossibile aprire il database '%.*ls' perché la versione è %d. Il server supporta la versione %d e precedenti. Il downgrade non è supportato.|  
  
## <a name="explanation"></a>Spiegazione  
Alcune caratteristiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] influiscono sulla struttura dei file di database. Quando si collega un database a un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile che il formato di file non sia compatibile con una versione diversa di [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
Ad esempio, questo errore può verificarsi quando si utilizza il formato di archiviazione vardecimal in una versione successiva di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e quindi si tenta di collegare i file del database in una versione precedente a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2.  
  
## <a name="user-action"></a>Azione dell'utente  
Verificare quale versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione nel server di origine. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fare clic con il pulsante destro del mouse sul server e quindi scegliere **Proprietà** oppure digitare **SELECT @@VERSION** in una finestra Query. Aprire il database utilizzando la versione originale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Verificare quali caratteristiche sono attivate nel database originale nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Modificare queste impostazioni in modo che venga utilizzata la versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui il database verrà collegato.  
  
