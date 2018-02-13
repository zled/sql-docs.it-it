---
title: Posta elettronica database e gli avvisi di posta elettronica con SQL Agent in Linux | Documenti Microsoft
description: In questo articolo viene descritto come utilizzare posta elettronica database e gli avvisi di posta elettronica con SQL Server in Linux
author: meet-bhagdev
ms.author: meetb
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: tbd
ms.workload: Inactive
ms.openlocfilehash: d5d9dd84a7c3489c96e4e1aeaeb6d0928140a83f
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="db-mail-and-email-alerts-with-sql-agent-on-linux"></a>Posta elettronica database e gli avvisi di posta elettronica con SQL Agent in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

La procedura seguente mostra come impostare posta elettronica database e usarlo con SQL Server Agent (**mssql-server agent**) in Linux. 

> [!NOTE]
> Per utilizzare posta elettronica database con SQL Server in Linux, è necessario utilizzare SQL Server 2017 RC1 o versioni successive.

## <a name="prerequisites"></a>Prerequisiti

- SQL Server 2017 RC1 e versioni successive
- SQL Server Agent v14.0.800.90-2 e versioni successive (se si prevede di utilizzare la posta elettronica per gli avvisi)

## <a name="1-enable-db-mail"></a>1. Abilitare posta elettronica database

```sql
USE master 
GO 
sp_configure 'show advanced options',1 
GO 
RECONFIGURE WITH OVERRIDE 
GO 
sp_configure 'Database Mail XPs', 1 
GO 
RECONFIGURE  
GO  
```

## <a name="2-create-a-new-account"></a>2. Crea nuovo account
```sql
EXECUTE msdb.dbo.sysmail_add_account_sp 
@account_name = 'SQLAlerts', 
@description = 'Account for Automated DBA Notifications', 
@email_address = 'sqlagenttest@gmail.com', 
@replyto_address = 'sqlagenttest@gmail.com', 
@display_name = 'SQL Agent', 
@mailserver_name = 'smtp.gmail.com', 
@port = 587, 
@enable_ssl = 1, 
@username = 'sqlagenttest@gmail.com', 
@password = '<password>' 
GO
```

## <a name="3-create-a-default-profile"></a>3. Creare un profilo predefinito

```sql
EXECUTE msdb.dbo.sysmail_add_profile_sp 
@profile_name = 'default', 
@description = 'Profile for sending Automated DBA Notifications' 
GO
```

## <a name="4-add-the-database-mail-account-to-a-database-mail-profile"></a>4. Aggiungere l'account di posta elettronica Database a un profilo di posta elettronica Database
```sql
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp 
@profile_name = 'default', 
@principal_name = 'public', 
@is_default = 1 ; 
 ```
 
## <a name="5-add-account-to-profile"></a>5. Aggiungere account al profilo 
```sql
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp   
@profile_name = 'default',   
@account_name = 'SQLAlerts',   
@sequence_number = 1;  
 ```
 
## <a name="6-send-test-email"></a>6. Invio di posta elettronica di test
> [!NOTE]
> Potrebbe essere necessario passare al client di posta elettronica e abilitare "Consenti client meno sicuri inviare posta elettronica." Non tutti i client riconoscono posta elettronica database come un daemon di posta elettronica.

```
EXECUTE msdb.dbo.sp_send_dbmail 
@profile_name = 'default', 
@recipients = 'recipient-email@gmail.com', 
@Subject = 'Testing DBMail', 
@Body = 'This message is a test for DBMail' 
GO
```

## <a name="7-set-db-mail-profile-using-mssql-conf-or-environment-variable"></a>7. Impostare il profilo di posta elettronica database utilizzando mssql conf o variabile di ambiente
È possibile utilizzare l'utilità mssql conf o variabili di ambiente per registrare il profilo di posta elettronica database. In questo caso, si parlerà predefinito il profilo.

```bash
# via mssql-conf
sudo /opt/mssq/bin/mssql-conf set sqlagent.databasemailprofile default
# via environment variable
MSSQL_AGENT_EMAIL_PROFILE=default
```

## <a name="8-set-up-an-operator-for-sqlagent-job-notifications"></a>8. Impostare un operatore per le notifiche di processo SQLAgent 

```sql
EXEC msdb.dbo.sp_add_operator 
@name=N'JobAdmins',  
@enabled=1, 
@email_address=N'recipient-email@gmail.com',  
@category_name=N'[Uncategorized]' 
GO 
```

## <a name="9-send-email-when-agent-test-job-succeeds"></a>9. Invia messaggio di posta elettronica al completamento 'Agente di Test del processo' 

```
EXEC msdb.dbo.sp_update_job 
@job_name='Agent Test Job', 
@notify_level_email=1, 
@notify_email_operator_name=N'JobAdmins' 
GO
```

## <a name="next-steps"></a>Passaggi successivi
Per ulteriori informazioni sull'utilizzo di SQL Server Agent per creare, pianificare ed eseguire processi, vedere [eseguire un processo di agente SQL Server in Linux](sql-server-linux-run-sql-server-agent-job.md).
