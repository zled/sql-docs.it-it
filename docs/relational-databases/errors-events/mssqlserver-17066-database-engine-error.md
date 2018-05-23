---
title: MSSQLSERVER_17066 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17066 (Database Engine error)
ms.assetid: 7d650bbf-c583-4af8-9e22-993ee2880d95
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dd503d14e1bcea86f155fd8926f87658deca94aa
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver17066"></a>MSSQLSERVER_17066
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17066|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLASSERT_ONLY|  
|Testo del messaggio|Asserzione SQL Server: file: \<%s>, riga=%d Asserzione non riuscita = '%s'. L'errore può essere correlato agli intervalli di tempo. Se dopo aver rieseguito l'istruzione l'errore persiste, utilizzare DBCC CHECKDB per verificare l'integrità strutturale del database oppure riavviare il server per verificare che le strutture di dati in memoria non siano danneggiate.|  
  
## <a name="explanation"></a>Spiegazione  
Questo errore può essere causato da errori temporanei, correlati agli intervalli di tempo o da un danno dei dati in memoria o su disco.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire nuovamente l'istruzione che ha causato l'attivazione dell'eccezione. Se l'errore è causato da un evento correlato agli intervalli di tempo, è possibile che non si ripeta. Se il problema persiste, eseguire DBCC CHECKDB per verificare il danno su disco. Riavviare il server per assicurarsi che le strutture di dati in memoria non siano danneggiate.  
  
## <a name="see-also"></a>Vedere anche  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  
