---
title: Impostare un database mirror crittografato | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cryptography [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- database master key [SQL Server], database mirroring
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7f51f7147850f5c20492fd7a83ec88006f87628d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166232"
---
# <a name="set-up-an-encrypted-mirror-database"></a>Impostazione di un database mirror crittografato

Per abilitare la decrittografia automatica della chiave master del database di un database mirror, è necessario fornire la password utilizzata per crittografare tale chiave nell'istanza del server mirror. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive includono meccanismi per trasferire la password. Usare **sp_control_dbmasterkey_password** per creare una credenziale per la chiave master del database prima di avviare il mirroring del database. Questa operazione va ripetuta per ogni database per il quale si desidera eseguire il mirroring. Per altre informazioni, vedere [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql).
  
> [!CAUTION]  
>  Non abilitare la decrittografia di failover di un database che deve rimanere inaccessibile a **sa** e altre entità server con privilegi elevati. È possibile configurare un database in modo che la sua gerarchia di chiavi non possa essere decrittografata dalla chiave master del servizio. Questa opzione viene supportata come difesa in profondità per database che contengono informazioni che non vanno rese accessibili a entità server **sa** o altre entità server con privilegi elevati. Abilitando la decrittografia di failover per un database di questo tipo si elimina questa difesa in profondità, consentendo a entità server **sa** e altre entità server con privilegi elevati di decrittografare il database.  


<!-- Note: We cannot append '?view=sql-server-2016' to these, even tho in theory we might want to. -->

## <a name="see-also"></a>Vedere anche

[sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)

[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)

[ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)

[Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)

[Impostazione del mirroring del database &#40;SQL Server&#41;](database-mirroring-sql-server.md)

