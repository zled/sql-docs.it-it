---
title: 'Esempio: Ripristino online di un file di sola lettura (modello di recupero con registrazione minima) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- restore sequences [SQL Server], online
- online restores [SQL Server], simple recovery model
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 0c691fc6-9865-46a7-b055-8097424492d6
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd720b4f1c2a897b5836cef516ee5b00342352e4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168557"
---
# <a name="example-online-restore-of-a-read-only-file-simple-recovery-model"></a>Esempio: Ripristino online di un file di sola lettura (modello di recupero con registrazione minima)
  Le informazioni in questo argomento sono rilevanti per i database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che utilizzano il modello di recupero con registrazione minima e che contengono un filegroup di sola lettura. Il modello di recupero con registrazione minima consente di ripristinare online un file di sola lettura, se è disponibile un backup del file eseguito dopo la prima conversione del file in file di sola lettura.  
  
 In questo esempio un database denominato `adb` contiene tre filegroup. Il filegroup `A` è di lettura/scrittura mentre i filegroup `B` e `C` sono di sola lettura. Inizialmente, tutti i filegroup sono online. È necessario ripristinare il file di sola lettura `B`del filegroup `b1`. Per ripristinarlo, l'amministratore del database può utilizzare un backup eseguito dopo che il file è diventato di sola lettura. Per tutta la durata del ripristino il filegroup `B` sarà offline, ma il resto del database resterà online.  
  
## <a name="restore-sequence"></a>Sequenza di ripristino  
  
> [!NOTE]  
>  La sintassi di una sequenza di ripristino online è la stessa di una sequenza di ripristino offline.  
  
 Per ripristinare il file, l'amministratore del database utilizza la sequenza di ripristino seguente:  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup   
WITH RECOVERY  
```  
  
 Il file è ora online.  
  
## <a name="additional-examples"></a>Esempi aggiuntivi  
  
-   [Esempio: Ripristino a fasi di un database &#40;modello di recupero con registrazione minima&#41;](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Esempio: Ripristino a fasi di filegroup selezionati &#40;modello di recupero con registrazione minima&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Esempio: Ripristino a fasi di un database &#40;modello di recupero con registrazione completa&#41;](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Esempio: Ripristino a fasi di un numero limitato di filegroup &#40;modello di recupero con registrazione completa&#41;](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Esempio: Ripristino online di un file di lettura/scrittura &#40;modello di recupero con registrazione completa&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Esempio: Ripristino online di un file di sola lettura &#40;modello di recupero con registrazione completa&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristino online &#40;SQL Server&#41;](online-restore-sql-server.md)   
 [Ripristini a fasi &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)   
 [Ripristini di file &#40;modello di recupero con registrazione minima&#41;](file-restores-simple-recovery-model.md)   
 [Panoramica del ripristino e del recupero &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
