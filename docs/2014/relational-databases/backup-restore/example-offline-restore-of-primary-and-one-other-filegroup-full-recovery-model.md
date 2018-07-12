---
title: 'Esempio: Ripristino Offline del filegroup primario e un altro Filegroup (modello di recupero con registrazione completa) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- offline restores [SQL Server]
- restore sequences [SQL Server], offline
ms.assetid: 7d6c50eb-dc84-4d66-855a-0b5f1bd89737
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d4a2a57a9f9f7046025ce2b5f2a8e0ba98ab63f3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37156372"
---
# <a name="example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model"></a>Esempio: Ripristino offline del filegroup primario e di un altro filegroup (modello di recupero con registrazione completa)
  Le informazioni contenute in questo argomento sono rilevanti solo per i database basati sul modello di recupero con registrazione completa che includono più filegroup.  
  
 In questo esempio un database denominato `adb` contiene tre filegroup. I filegroup `A` e `C` sono di lettura/scrittura, mentre il filegroup `B` è di sola lettura. Il filegroup primario e il filegroup `B` sono danneggiati, mentre i filegroup `A` e `C` sono integri. Prima dell'emergenza, tutti i filegroup erano online.  
  
 L'amministratore del database decide di ripristinare e recuperare il filegroup primario e il filegroup `B`. Dato che il database utilizza il modello di recupero con registrazione completa, prima dell'avvio del ripristino è necessario eseguire un backup della parte finale del log per il database. Non appena il database è online, viene attivata automaticamente la modalità online per i filegroup `A` e `C` .  
  
> [!NOTE]  
>  La sequenza di ripristino offline prevede un numero di passaggi inferiore rispetto al ripristino online di un file di sola lettura. Per un esempio, vedere [Esempio: Ripristino in linea di un file di sola lettura &#40;modello di recupero con registrazione completa&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md). L'intero database, tuttavia, rimane in modalità offline per tutta la durata della sequenza.  
  
## <a name="tail-log-backup"></a>Backup della parte finale del log  
 Prima di ripristinare il database, è necessario che l'amministratore del database esegua il backup della parte finale del log. Dato che il database è danneggiato, la creazione di tale backup richiede l'utilizzo dell'opzione NO_TRUNCATE:  
  
```  
BACKUP LOG adb TO tailLogBackup   
   WITH NORECOVERY, NO_TRUNCATE  
```  
  
 Il backup della parte finale del log è l'ultimo backup applicato nelle sequenze di ripristino seguenti.  
  
## <a name="restore-sequence"></a>Sequenza di ripristino  
 Per ripristinare il filegroup primario e il filegroup `B`, l'amministratore del database utilizza una sequenza di ripristino senza l'opzione PARTIAL, come illustrato di seguito:  
  
```  
RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
WITH NORECOVERY  
RESTORE DATABASE adb FILEGROUP='B' FROM backup2   
WITH NORECOVERY  
RESTORE LOG adb FROM backup3 WITH NORECOVERY  
RESTORE LOG adb FROM backup4 WITH NORECOVERY  
RESTORE LOG adb FROM backup5 WITH NORECOVERY  
RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
```  
  
 Per i file non ripristinati viene attivata automaticamente la modalità online. Tutti i filegroup sono ora online.  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristino online &#40;SQL Server&#41;](online-restore-sql-server.md)   
 [Ripristini a fasi &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)   
 [Ripristini di file &#40;modello di recupero con registrazione completa&#41;](file-restores-full-recovery-model.md)   
 [Applicare backup del log delle transazioni &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
