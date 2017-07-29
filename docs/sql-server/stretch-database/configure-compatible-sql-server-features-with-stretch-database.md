---
title: "Configurare le funzionalità compatibili di SQL Server con Estensione database | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8121ede-1aec-459b-b7b0-1408bb3e62fb
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 84464c4553eab6d8e65c0bf6b476ae728e2a8463
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="configure-compatible-sql-server-features-with-stretch-database"></a>Configurare le funzionalità compatibili di SQL Server con Estensione database
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Per configurare le seguenti funzionalità di SQL Server per il funzionamento con Estensione database sono sufficienti alcuni semplici passaggi.
-   Always On
-   Crittografia sempre attiva
-   Transparent Data Encryption (TDE)
-   Tabelle temporali

## <a name="configure-always-on-with-stretch-database"></a>Configurare Always On con Estensione database
Se si usa Always On con Estensione database, è necessario verificare che la chiave master del database sia disponibile nelle repliche secondarie. Estensione database usa la chiave master del database per proteggere le credenziali che usa per la connessione al database remoto.

Dopo aver configurato il gruppo di disponibilità Always On, eseguire la stored procedure **sp_control_dbmasterkey_password** in ogni replica secondaria e specificare la password per il database abilitato per l'estensione. Per altre informazioni ed esempi, vedere [sp_control_dbmasterkey_password](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md). 

## <a name="configure-always-encrypted-with-stretch-database"></a>Configurare Always Encrypted con Estensione database
Se si vuole usare Always Encrypted insieme a Estensione database, è necessario configurare la crittografia nelle colonne selezionate prima di abilitare Estensione database nella tabella.

Se la funzionalità Estensione database è già abilitata nella tabella e si vogliono usare colonne Always Encrypted, è necessario effettuare le operazioni seguenti.
1.   Disabilitare Estensione database nella tabella e recuperare i dati remoti da Azure. Per altre informazioni, vedere [Disabilitare Estensione database e ripristinare i dati remoti](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).
2.   Configurare Always Encrypted nelle colonne selezionate.
3. Abilitare nuovamente Estensione database nella tabella. Per ulteriori informazioni, vedere [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).

## <a name="configure-transparent-data-encryption-tde-with-stretch-database"></a>Configurare Transparent Data Encryption (TDE) con Estensione database

Se la crittografia TDE è abilitata nel database locale, non verrà abilitata automaticamente nell'endpoint remoto di Estensione database. È necessario ricordarsi di abilitare la crittografia TDE nell'endpoint remoto dopo avere abilitato l'estensione nel database.

## <a name="configure-temporal-tables-with-stretch-database"></a>Configurare le tabelle temporali con Estensione database
Se si usano le tabelle temporali, è possibile abilitare Estensione database nella tabella di cronologia, ma non nella tabella corrente.
-   Per istruzioni sull'uso delle tabelle temporali con Estensione database, vedere [Gestire la conservazione dei dati cronologici nelle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md).
-   Per filtrare le righe di cui eseguire la migrazione dalla tabella di cronologia usando una finestra temporale scorrevole, vedere [Selezionare le righe di cui eseguire la migrazione tramite una funzione di filtro](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).
