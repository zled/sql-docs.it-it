---
title: MSSQLSERVER_3452 | Microsoft Docs
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
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 61fbabc84b9ef22a7275faa4ab2c04b208466193
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver3452"></a>MSSQLSERVER_3452
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|3452|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|REC_CHECKIDENTITY|  
|Testo del messaggio|Durante il recupero del database '%.*ls' (%d) è stata rilevata una possibile inconsistenza dei valori Identity nella tabella con ID %d. Eseguire DBCC CHECKIDENT ('%.\*ls').|  
  
## <a name="explanation"></a>Spiegazione  
Durante l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], nel processo di recupero dei valori Identity nel database è stata rilevata un'incoerenza tra i metadati.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire DBCC CHECKIDENT.  
  

