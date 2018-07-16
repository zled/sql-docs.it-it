---
title: Eseguire gli script prima e dopo l'applicazione dello snapshot | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], scripts
- scripts [SQL Server replication], snapshots
- snapshot replication [SQL Server], scripts
- scripts [SQL Server replication]
ms.assetid: 9a6872c2-9bed-477f-9d2f-332d640edcf2
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fde608be7281ca66856f63db3a2626863c1a30f1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320051"
---
# <a name="execute-scripts-before-and-after-the-snapshot-is-applied"></a>Eseguire gli script prima e dopo l'applicazione dello snapshot
  È possibile specificare gli script da eseguire nel Sottoscrittore prima o dopo l'applicazione dello snapshot. È possibile utilizzare script per diversi scopi, ad esempio per creare account di accesso e schemi (proprietari di oggetti) in ogni Sottoscrittore.  
  
 Dopo avere specificato un percorso per ogni script, l'agente snapshot copia i file script nella cartella snapshot corrente ogni volta che viene eseguita l'elaborazione dello snapshot. Quando si applica uno snapshot, l'agente di distribuzione o l'agente di merge esegue lo script pre-snapshot prima di qualsiasi script degli oggetti replicati. L'agente di distribuzione o l'agente di merge esegue lo script post-snapshot dopo l'applicazione di tutti gli altri script degli oggetti replicati e dei dati. Al termine dell'applicazione dello snapshot e dell'esecuzione corretta dei file script, gli script vengono rimossi dalla directory di lavoro del Sottoscrittore.  
  
 Lo script viene eseguito avviando l'utilità **sqlcmd** . Prima di distribuire uno script, eseguirlo con **sqlcmd** per verificarne la corretta esecuzione in base a quanto previsto. È necessario che il contenuto degli script eseguiti prima e dopo l'applicazione dello snapshot sia ripetibile. Se, ad esempio, si crea una tabella nello script, è innanzitutto necessario verificarne l'esistenza e, in tal caso, eseguire le azioni appropriate. Lo script deve essere ripetibile perché, se è necessario reinizializzare una sottoscrizione per cui lo script è già stato applicato, lo script viene applicato nuovamente in corrispondenza dell'applicazione del nuovo snapshot in fase di reinizializzazione.  
  
 Se il file di snapshot viene compresso in formato [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB, vengono compressi e inclusi nel file CAB anche gli script. Dopo il trasferimento e la decompressione del file di snapshot compresso in una directory di lavoro nel Sottoscrittore, vengono eseguiti tutti gli script indicati come pre-snapshot. In modo analogo, tutti gli script post-snapshot vengono decompressi ed eseguiti nel Sottoscrittore come ultimo passaggio dell'applicazione dello snapshot.  
  
 **Per eseguire gli script prima e dopo l'applicazione dello snapshot**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Procedura: Eseguire gli script prima e dopo l'applicazione dello snapshot \(SQL Server Management Studio\)](execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   Programmazione [!INCLUDE[tsql](../../includes/tsql-md.md)] della replica: [Configurare le proprietà dello snapshot &#40;programmazione Transact-SQL della replica&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Inizializzare una sottoscrizione con uno snapshot](initialize-a-subscription-with-a-snapshot.md)   
 [Opzioni per gli snapshot](snapshot-options.md)  
  
  
