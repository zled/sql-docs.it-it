---
title: Chiave master del servizio | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service master key [SQL Server]
- service master key [SQL Server], about service master key
ms.assetid: 85f2095d-2590-4f59-8a29-7e100edd02bb
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fd1adfac8a64c19577374d309390bead0cb12de9
ms.lasthandoff: 04/11/2017

---
# <a name="service-master-key"></a>Chiave master del servizio
  La chiave master del servizio è la radice della gerarchia di crittografia di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e viene generata automaticamente la prima volta che risulta necessaria per crittografare un'altra chiave. Per impostazione predefinita, la chiave master del servizio viene crittografata mediante l'API Windows per la protezione dei dati e la chiave del computer locale. La chiave master del servizio può essere aperta solo dall'account di servizio Windows nel quale è stata creata oppure da un'entità con accesso sia al nome che alla password del'account di servizio.  
  
 Per rigenerare o ripristinare la chiave master del servizio è necessario decrittografare e crittografare nuovamente l'intera gerarchia di crittografia. Poiché questa operazione utilizza molte risorse, è opportuno programmarla durante un periodo di bassa richiesta, a meno che la chiave non sia compromessa.  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] usa l'algoritmo di crittografia AES per proteggere la chiave master del servizio (SMK) e la chiave master del database (DMK). AES è un algoritmo di crittografia più recente rispetto a 3DES utilizzato nelle versioni precedenti. Dopo aver aggiornato un'istanza di [!INCLUDE[ssDE](../../../includes/ssde-md.md)] a [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] le chiavi SMK e DMK devono essere rigenerate per aggiornare le chiavi master ad AES. Per altre informazioni sulla rigenerazione della chiave SMK, vedere [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-service-master-key-transact-sql.md) e [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-master-key-transact-sql.md).  
  
## <a name="best-practice"></a>Procedura consigliata  
 Eseguire il backup della chiave master del servizio e archiviare la copia di backup in un altro luogo adeguatamente protetto.  
  
## <a name="related-tasks"></a>Attività correlate  
 [BACKUP SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/backup-service-master-key-transact-sql.md)  
  
 [RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/restore-service-master-key-transact-sql.md)  
  
 [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-service-master-key-transact-sql.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia di crittografia](../../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
