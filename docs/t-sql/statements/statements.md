---
title: Istruzioni | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d8d6f62a-e815-425c-a80e-a63fd34ec275
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5b7daa257b6a6afca3bd3aa8a1c09b08e0fb5778
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34582123"
---
# <a name="transact-sql-statements"></a>istruzioni Transact-SQL
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

Questo argomento di riferimento riepiloga le categorie di istruzioni da usare con Transact-SQL (T-SQL). L'elenco completo delle istruzioni è visualizzato nell'area di navigazione a sinistra.

## <a name="backup-and-restore"></a>Backup e ripristino
Le istruzioni backup e ripristino consentono di creare backup e di eseguire il ripristino dai backup.  Per altre informazioni, vedere [Backup and restore overview](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md) (Panoramica su backup e ripristino).

## <a name="data-definition-language"></a>Data Definition Language
Le istruzioni DDL (Data Definition Language) definiscono le strutture dei dati. Usare queste istruzioni per creare, modificare o eliminare le strutture dei dati in un database.
- ALTER
- Regole di confronto
- CREATE
- DROP
- DISABLE TRIGGER
- ENABLE TRIGGER
- RENAME
- UPDATE STATISTICS

## <a name="data-manipulation-language"></a>Data Manipulation Language
Le istruzioni Data Manipulation Language (DML) hanno effetto sulle informazioni archiviate nel database. Usare queste istruzioni per inserire, aggiornare e modificare le righe nel database.

- BULK INSERT
- Elimina
- INSERT
- UPDATE
- MERGE
- TRUNCATE TABLE

## <a name="permissions-statements"></a>Istruzioni di autorizzazioni
Le istruzioni di autorizzazioni determinano quali utenti e account di accesso possono accedere ai dati ed eseguire operazioni. Per altre informazioni sull'autenticazione e l'accesso, vedere [Centro sicurezza](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="service-broker-statements"></a>Istruzioni di Service Broker
Service Broker è una funzionalità che offre supporto nativo per le applicazioni di messaggistica e accodamento. Per altre informazioni, vedere [Service Broker](../../relational-databases/service-broker/event-notifications.md).

## <a name="session-settings"></a>Impostazioni sessione
Le istruzioni SET determinano come la sessione corrente gestisce le impsotazioni di runtime. Per una panoramica, vedere [Istruzioni SET](set-statements-transact-sql.md).
