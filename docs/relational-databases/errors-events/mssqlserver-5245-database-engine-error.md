---
title: MSSQLSERVER_5245 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: d1ee9b94e955cd560db165e774d623dbf2796aeb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver5245"></a>MSSQLSERVER_5245
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|5245|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|Testo del messaggio|ID oggetto O_ID (oggetto 'NAME'): DBCC non è in grado di ottenere un blocco sull'oggetto. Timeout della richiesta di blocco. L'oggetto è stato ignorato e non verrà elaborato.|  
  
## <a name="explanation"></a>Spiegazione  
Si è verificato un timeout di blocco mentre DBCC era in attesa di un blocco a livello di tabella per l'oggetto specificato.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire di nuovo il comando DBCC.  
  
