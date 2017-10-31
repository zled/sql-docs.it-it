---
title: MSSQLSERVER_4064 | Microsoft Docs
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
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ff8f948a1c94fcfcb36f43d0644e251e027a02c5
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver4064"></a>MSSQLSERVER_4064
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|4064|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DB_UFAIL_FATAL|  
|Testo del messaggio|Impossibile aprire il database utente predefinito. Accesso non riuscito.|  
  
## <a name="explanation"></a>Spiegazione  
L'account di accesso di SQL Server non è in grado di connettersi a causa di un problema con il relativo database predefinito. Il database non è valido oppure l'account di accesso non dispone dell'autorizzazione CONNECT per il database.  
  
## <a name="user-action"></a>Azione dell'utente  
Utilizzare ALTER LOGIN per modificare il database predefinito dell'account di accesso. Concedere l'autorizzazione CONNECT all'account di accesso.  
  

