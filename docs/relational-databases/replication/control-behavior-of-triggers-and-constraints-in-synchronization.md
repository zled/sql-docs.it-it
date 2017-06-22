---
title: Controllare il comportamento di trigger e vincoli nella sincronizzazione | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 24825a3c9c016588b4ac3d1a9c8fa29741e609b3
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="control-behavior-of-triggers-and-constraints-in-synchronization"></a>Controllare il comportamento di trigger e vincoli nella sincronizzazione
  Durante la sincronizzazione gli agenti di replica eseguono istruzioni [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md), [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md) e [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md) in tabelle replicate che possono causare l'esecuzione di trigger DML (Data Manipulation Language) in tali tabelle. In alcuni casi è necessario impedire l'attivazione di questi trigger o l'applicazione di vincoli durante la sincronizzazione. Questo comportamento dipende dalla modalità di creazione del trigger o del vincolo.  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a>Per impedire l'esecuzione di trigger durante la sincronizzazione  
  
1.  Quando si crea un nuovo trigger, specificare l'opzione NOT FOR REPLICATION di [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md).  
  
2.  Per un trigger esistente specificare l'opzione NOT FOR REPLICATION di [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md).  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a>Per impedire l'applicazione di vincoli durante la sincronizzazione  
  
1.  Quando si crea un nuovo vincolo CHECK o FOREIGN KEY, specificare l'opzione CHECK NOT FOR REPLICATION nella definizione del vincolo di [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creare tabelle &#40;Motore di database&#41;](../../relational-databases/tables/create-tables-database-engine.md)  
  
  
