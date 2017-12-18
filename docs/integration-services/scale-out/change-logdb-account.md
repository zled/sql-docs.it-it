---
title: Modificare l'account per la registrazione di SSIS Scale Out | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dcedbe0d2c2ef2c2089af1e2a8b31fbeb75ce2fc
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="change-the-account-for-scale-out-logging"></a>Modificare l'account per la registrazione di Scale Out
Durante l'esecuzione di pacchetti in Scale Out, i messaggi di evento vengono registrati in SSISDB con un **##MS_SSISLogDBWorkerAgentLogin##** creato automaticamente. L'account di accesso di questo utente usa l'autenticazione di SQL Server. Per cambiare l'account, seguire questa procedura:

## <a name="1-create-a-user-of-ssisdb"></a>1. Creare un utente di SSISDB
Per istruzioni per la creazione di un utente del database, vedere [Creare un utente del database](../../relational-databases/security/authentication-access/create-a-database-user.md).

## <a name="2-add-the-user-to-database-role-ssisclusterworker"></a>2. Aggiungere l'utente al ruolo del database ssis_cluster_worker

Per istruzioni per l'aggiunta di un ruolo del database, vedere [Aggiungere un ruolo](../../relational-databases/security/authentication-access/join-a-role.md).

## <a name="3-update-logging-information-in-ssisdb"></a>3. Aggiornare le informazioni di registrazione in SSISDB
Chiamare la stored procedure [catalog].[update_logdb_info] con il nome del server SQL e la stringa di connessione come parametri.

#### <a name="example"></a>Esempio
```sql
SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
EXEC [internal].[update_logdb_info] @serverName, @connectionString
GO
```

## <a name="4-restart-scale-out-worker-service"></a>4. Riavviare il servizio Scale Out Worker

> [!NOTE]
> Se si usa un account utente di Windows per la registrazione, deve essere lo stesso account che esegue il servizio Scale Out Worker. In caso contrario, l'accesso al server SQL non riuscirà.
