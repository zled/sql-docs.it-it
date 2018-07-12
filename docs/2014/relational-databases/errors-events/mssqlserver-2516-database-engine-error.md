---
title: MSSQLSERVER_2516 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f82719e1227271a993cb55fba53623170baec38c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418800"
---
# <a name="mssqlserver2516"></a>MSSQLSERVER_2516
    
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
 [Creazione di un backup completo del database &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
  
