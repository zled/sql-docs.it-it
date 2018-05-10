---
title: MSSQLSERVER_17067 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17067 (Database Engine error)
ms.assetid: 32c1f0e8-db70-4836-95b2-8833be9e0ad1
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c6c35aadefe56c4c9487bf901ff4a13b082375ff
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17067"></a>MSSQLSERVER_17067
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17067|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLASSERT_MESG|  
|Testo del messaggio|Asserzione SQL Server: file: \<%s>, line = %d %s. L'errore può essere correlato agli intervalli di tempo. Se dopo aver rieseguito l'istruzione l'errore persiste, utilizzare DBCC CHECKDB per verificare l'integrità strutturale del database oppure riavviare il server per verificare che le strutture di dati in memoria non siano danneggiate.|  
  
## <a name="explanation"></a>Spiegazione  
Questo errore può essere causato da errori temporanei, correlati agli intervalli di tempo o da un danno dei dati in memoria o su disco.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire nuovamente l'istruzione che ha causato l'attivazione dell'eccezione. Se l'errore è causato da un evento correlato agli intervalli di tempo, è possibile che non si ripeta. Se il problema persiste, eseguire DBCC CHECKDB per verificare il danno su disco. Riavviare il server per assicurarsi che le strutture di dati in memoria non siano danneggiate.  
  
## <a name="see-also"></a>Vedere anche  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  
