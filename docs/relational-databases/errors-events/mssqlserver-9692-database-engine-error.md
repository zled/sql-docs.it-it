---
title: MSSQLSERVER_9692 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 970733fb1f494b201e0bffa3f88aa27de4465cbf
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver9692"></a>MSSQLSERVER_9692
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|9692|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SB2_CANT_LISTEN_PORT_IN_USE|  
|Testo del messaggio|Il trasporto di protocollo %S_MSG non può restare in attesa sulla porta %d perché è in uso da un altro processo.|  
  
## <a name="explanation"></a>Spiegazione  
Un altro programma in esecuzione nel computer sta utilizzando la porta TCP indicata.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire **netstat -aon** per determinare quale programma sta usando la porta. Disabilitare l'applicazione oppure specificare una porta diversa per Service Broker.  
  

