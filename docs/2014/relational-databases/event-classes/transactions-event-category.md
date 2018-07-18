---
title: Categoria di eventi Transazioni | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0322fd84cf708b8310b7ec6e1483ae24d998617e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166962"
---
# <a name="transactions-event-category"></a>Categoria di eventi Transactions
  Le classi di eventi della categoria **Transactions** consentono di monitorare lo stato delle transazioni. I nomi delle classi di eventi con prefisso **TM:** sono utilizzati per tracciare le operazioni correlate alle transazioni che vengano inviate tramite l'interfaccia di gestione delle transazioni.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Classe di evento DTCTransaction](dtctransaction-event-class.md)|Tiene traccia delle transazioni coordinate da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC). Si tratta delle transazioni distribuite tra due o più database o istanze di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Classe di evento SQLTransaction](sqltransaction-event-class.md)|Tiene traccia delle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN e ROLLBACK TRAN.|  
|[Classe di evento TM: Begin Tran Completed](tm-begin-tran-completed-event-class.md)|Indica il completamento di una richiesta BEGIN TRANSACTION.|  
|[Classe di evento TM: Begin Tran Starting](tm-begin-tran-starting-event-class.md)|Indica l'avvio di una richiesta BEGIN TRANSACTION.|  
|[Classe di evento TM: Commit Tran Completed](tm-commit-tran-completed-event-class.md)|Indica il completamento di una richiesta COMMIT TRANSACTION.|  
|[Classe di evento TM: Commit Tran Starting](tm-commit-tran-starting-event-class.md)|Indica l'avvio di una richiesta COMMIT TRANSACTION.|  
|[Classe di evento TM: Promote Tran Completed](tm-promote-tran-completed-event-class.md)|Indica il completamento di una richiesta PROMOTE TRANSACTION.|  
|[Classe di evento TM: Promote Tran Starting](tm-promote-tran-starting-event-class.md)|Indica l'avvio di una richiesta PROMOTE TRANSACTION.|  
|[Classe di evento TM: Rollback Tran Completed](tm-rollback-tran-completed-event-class.md)|Indica il completamento di una richiesta ROLLBACK TRANSACTION.|  
|[Classe di evento TM: Rollback Tran Starting](tm-rollback-tran-starting-event-class.md)|Indica l'avvio di una richiesta ROLLBACK TRANSACTION.|  
|[Classe di evento TM: Save Tran Completed](tm-save-tran-completed-event-class.md)|Indica il completamento di una richiesta SAVE TRANSACTION.|  
|[Classe di evento TM: Save Tran Starting](tm-save-tran-starting-event-class.md)|Indica l'avvio di una richiesta SAVE TRANSACTION.|  
|[Classe di evento TransactionLog](transactionlog-event-class.md)|Traccia l'inserimento delle transazioni in un log delle transazioni di database.|  
  
  
