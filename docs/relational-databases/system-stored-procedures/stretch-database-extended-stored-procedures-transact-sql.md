---
title: Estensione Database (Transact-SQL) di Stored procedure esteso | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Stretch Database, stored procedures
ms.assetid: bda29952-4b8b-4295-ab78-f24dcb0b03c6
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e302aba2baf35f7a01f7242b2fa0eaaad45ee18f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="stretch-database-extended-stored-procedures-transact-sql"></a>Estensione Database Extended Stored procedure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 In questa sezione vengono descritte le stored procedure estese che riguardano l'estensione Database.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
[Sys. sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md) rimuove la connessione autenticata tra un database locale abilitata per l'estensione e sul database Azure remoto.

[sp_rda_get_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md) Ottiene il numero di ore dei dati migrati che SQL Server vengono mantenuti in una tabella di gestione temporanea al fine di garantire un ripristino completo del database Azure remoto, se è necessario un ripristino.
  
 [Sys. sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) Ripristina la connessione autenticata tra un database locale abilitato per l'estensione e il database remoto.
  
 [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md)  
 Riconcilia ID batch archiviati nella tabella SQL Server abilitata per l'estensione per i dati migrati più di recente con l'ID batch archiviato nella tabella di Azure remota. 
 
[sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md) Riconcilia le colonne nella tabella di Azure remota alle colonne di tabella abilitata per l'estensione SQL Server.
 
 [Sys.sp_rda_reconcile_indexes](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-indexes-transact-sql.md) accodata un'attività di schema per riconciliare gli indici della tabella remota.
 
 [sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) specifica se le query sui database abilitati per estensione corrente e le relative tabelle restituiscono dati locali e remoti (impostazione predefinita) o solo i dati locali.
 
 [Sys. sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md) imposta il numero di ore dei dati migrati che SQL Server vengono mantenuti in una tabella di gestione temporanea al fine di garantire un ripristino completo del database Azure remoto, se è necessario un ripristino.
 
 [Sys.sp_rda_test_connection](../../relational-databases/system-stored-procedures/sys-sp-rda-test-connection-transact-sql.md) verifica la connessione da SQL Server per il server Azure remoto e segnala i problemi che potrebbero impedire la migrazione dei dati.
 
## <a name="see-also"></a>Vedere anche  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
