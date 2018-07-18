---
title: MSSQLSERVER_2516 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c42dd135eace8e81b2423e2e70e4c09eb6baf1b0
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver2516"></a>MSSQLSERVER_2516
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2516|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_REPAIR_DIFF_MAP_INVALIDATED|  
|Testo del messaggio|La correzione ha invalidato la mappa di bit differenziale per il database NAME. La catena di backup differenziale è stata interrotta. Prima di eseguire un backup differenziale è necessario eseguire un backup completo del database.|  
  
## <a name="explanation"></a>Spiegazione  
Questo messaggio informativo viene restituito quando si corregge l'errore MSSQLEngine_2515.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire un backup completo del database.  
  
## <a name="see-also"></a>Vedere anche  
[Creazione di un backup completo del database &#40;SQL Server&#41;](~/relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
