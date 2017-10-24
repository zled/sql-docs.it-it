---
title: CHECKPOINT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKPOINT_TSQL
- CHECKPOINT
dev_langs:
- TSQL
helpviewer_keywords:
- events [SQL Server], checkpoints
- automatic checkpoints
- writing dirty pages to disk
- pages [SQL Server], dirty
- checkpoints [SQL Server]
- CHECKPOINT statement
- log truncate mode [SQL Server]
- dirty pages
- logs [SQL Server], checkpoints
- manual checkpoints [SQL Server]
- pages [SQL Server], checkpoints
ms.assetid: ccdfc689-ad4e-44c0-83f7-0f2cfcfb6406
caps.latest.revision: 59
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d3c0dd607231880ebd7a43b3740eb2cb22b9c195
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="checkpoint-transact-sql"></a>CHECKPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Genera un checkpoint manuale nel database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al quale l'utente è attualmente connesso.  
  
> [!NOTE]  
>  Per informazioni sui diversi tipi di checkpoint di database e l'operazione di checkpoint in generale, vedere [checkpoint di Database &#40; SQL Server &#41; ](../../relational-databases/logs/database-checkpoints-sql-server.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CHECKPOINT [ checkpoint_duration ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *checkpoint_duration*  
 Specifica il numero di secondi disponibili per il completamento manuale del checkpoint. Quando *checkpoint_duration* è specificato, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] tenta di eseguire il checkpoint nell'arco di tempo. Il *checkpoint_duration* deve essere un'espressione di tipo **int** e deve essere maggiore di zero. Se si omette questo parametro, tramite il [!INCLUDE[ssDE](../../includes/ssde-md.md)] viene adeguata automaticamente la durata del checkpoint per ridurre al minimo l'impatto sulle prestazioni nelle applicazioni di database. *checkpoint_duration* è un'opzione avanzata.  
  
## <a name="factors-affecting-the-duration-of-checkpoint-operations"></a>Fattori che incidono sulla durata delle operazioni di checkpoint  
 In generale il tempo necessario per l'esecuzione di un'operazione di checkpoint aumenta con il numero di pagine dirty che l'operazione deve scrivere. Per impostazione predefinita, per ridurre l'impatto sulle prestazioni su altre applicazioni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene regolata la frequenza di scritture che un'operazione di checkpoint esegue. Se si riduce la frequenza delle scritture, aumenta il tempo necessario per completare l'operazione di checkpoint. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]utilizza questa strategia per un checkpoint manuale, a meno che un *checkpoint_duration* sia stato specificato nel comando CHECKPOINT.  
  
 L'impatto sulle prestazioni dell'utilizzo di *checkpoint_duration* dipende dal numero di pagine dirty, l'attività sul sistema e la durata effettiva specificata. Ad esempio, se il checkpoint viene normalmente completato in 120 secondi, specificando un *checkpoint_duration* su 45 secondi, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di dedicare più risorse per il checkpoint di quante ne verrebbero assegnate per impostazione predefinita. Al contrario, specificare un *checkpoint_duration* su 180 secondi causerebbe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assegna meno risorse di quante ne verrebbero assegnate per impostazione predefinita. In generale, un breve *checkpoint_duration* aumenterà le risorse dedicate al checkpoint, mentre un *checkpoint_duration* consente di ridurre le risorse dedicate al checkpoint. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un checkpoint, se possibile, viene sempre completato e l'istruzione CHECKPOINT restituisce immediatamente un risultato al completamento del checkpoint. In alcuni casi, quindi, un checkpoint può venire completato prima o dopo il periodo di tempo indicato.  
  
##  <a name="Security"></a> Sicurezza  
  
### <a name="permissions"></a>Permissions  
 Autorizzazioni CHECKPOINT per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server e **db_owner** e **db_backupoperator** ruoli predefiniti del database e non sono possono essere trasferite.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Checkpoint di database &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [Configurare l'opzione di configurazione Server recovery interval](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)   
 [ARRESTO &#40; Transact-SQL &#41;](../../t-sql/language-elements/shutdown-transact-sql.md)  
  
  

