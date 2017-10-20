---
title: Modificare l'account per la registrazione SSIS Scale Out | Documenti Microsoft
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ec785459e5f9585776d83cde3f460c1e79367e46
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="change-the-account-for-scale-out-logging"></a>Modificare l'account per la registrazione orizzontale
Quando l'esecuzione di pacchetti in orizzontale, i messaggi di evento vengono registrati in SSISDB a un utente create automaticamente **MS_SSISLogDBWorkerAgentLogin # # # #**. L'account di accesso dell'utente utilizza l'autenticazione di SQL Server. Per modificare l'account indicato di seguito i passaggi seguenti:

## <a name="1-create-a-user-of-ssisdb"></a>1. Creare un utente di SSISDB
Per istruzioni di creazione di un utente del database, vedere [creare un utente del Database](../../relational-databases/security/authentication-access/create-a-database-user.md).

## <a name="2-add-the-user-to-database-role-ssisclusterworker"></a>2. Aggiungere l'utente ssis_cluster_worker ruolo database

Per istruzioni di un join di un ruolo del database, vedere [aggiungere un ruolo](../../relational-databases/security/authentication-access/join-a-role.md).

## <a name="3-update-logging-information-in-ssisdb"></a>3. Aggiornare le informazioni di registrazione in SSISDB
Chiamare stored procedure [catalog]. [update_logdb_info] con stringa di connessione e nome di Sql Server come parametri.

#### <a name="example"></a>Esempio
```sql
SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
EXEC [internal].[update_logdb_info] @serverName, @connectionString
GO
```

## <a name="4-restart-scale-out-worker-service"></a>4. Riavviare il servizio di scala Out lavoro

> [!NOTE]
> Se si utilizza un account utente di Windows per la registrazione, deve essere lo stesso account che esegue il servizio di scala il lavoro. In caso contrario, l'account di accesso a SQL Server avrà esito negativo.
