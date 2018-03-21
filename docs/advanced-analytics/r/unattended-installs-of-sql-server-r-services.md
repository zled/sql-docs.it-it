---
title: Installazione automatica di Machine Learning Services | Documenti Microsoft
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: f1c7aaf35c0c58e9a7aab3c5b31725f586ffd2ac
ms.sourcegitcommit: 6bd21109abedf64445bdb3478eea5aaa7553fa46
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2018
---
# <a name="unattended-installation-of-machine-learning-services-in-database"></a>Installazione automatica di Machine Learning Services (In-Database)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene descritto come utilizzare gli argomenti della riga di comando con l'installazione di SQL Server per installare i componenti di apprendimento.

Per l'installazione automatica, si intende non utilizzare le funzionalità interattive dell'installazione guidata e invece fornire tutti gli argomenti necessari per completare l'installazione, incluse le licenze contratti per SQL Server e per i componenti di machine learning in un riga di comando o come parte di uno script, in genere in modalità non interattiva.

+ [SQL Server 2016 R Services](#bkmk_OldInstall)
+ [SQL Server 2017 apprendimento servizi](#bkmk_NewInstall) con Python o R
+ [Microsoft R Server o Server di Machine Learning](../r/install-microsoft-r-server-from-the-command-line.md)

**Si applica a: SQL Server 2017 servizi Machine Learning (In-Database), SQL Server 2016 R Services**

## <a name="prerequisites"></a>Prerequisiti

+ È necessario installare il motore di database in ogni istanza in cui si utilizzerà l'apprendimento automatico.

+ Se il computer non ha accesso a Internet, assicurarsi di scaricare i programmi di installazione per l'apprendimento automatico dei componenti in anticipo. Vedere [installazione dei componenti di machine learning senza accesso a Internet](../r/installing-ml-components-without-internet-access.md).

+ Esistono separate le licenze di parametri per ognuno dei componenti di origine aperti di R e Python. SQL Server 2016 supporta solo R; SQL Server 2017 supporta R e Python. È necessario accettare le condizioni di licenza per ogni lingua da installare. L'installazione non riesce se questo parametro non incluso nella riga di comando.

+ Per completare l'installazione senza la necessità di rispondere ai prompt, assicurarsi di aver identificato tutti gli argomenti obbligatori, incluse quelle per le licenze e per le altre funzionalità che si potrebbero voler installare.

+ Il **Mixed** modalità di sicurezza che supporta gli account di accesso SQL accadeva nelle prime versioni. Anche se non è più necessario, è possibile abilitare l'autenticazione modalità mista supportare lo sviluppo di soluzioni dagli esperti di dati che utilizzano un account di accesso SQL.

> [!IMPORTANT]
> 
> Dopo il completamento dell'installazione per abilitare la funzionalità, sono necessari passaggi aggiuntivi. Sono inclusi una riconfigurazione e riavvio dell'istanza. Assicurarsi di esaminare tutti gli elementi nella sezione nella [passaggi successivi all'installazione](#bkmk_PostInstall) per determinare le azioni necessarie al termine dell'installazione.

## <a name="bkmk_NewInstall"></a>  Installazione della riga di comando per SQL Server 2017

Negli esempi seguenti includono le **minimo** funzionalità necessarie.

> [!IMPORTANT]
> Assicurarsi di eseguire tutti i comandi da un prompt dei comandi con privilegi elevati.
> 
> Al termine dell'installazione, sono richiesti alcuni passaggi aggiuntivi. Vedere [in questa sezione](#bkmk_PostInstall). 
> Un altro riavvio dei servizi di SQL Server è necessario specificare al termine della configurazione.

### <a name="install-r-only"></a>Solo installazione R

Nell'esempio seguente viene illustrato come installare gli argomenti necessari per eseguire un invisibile all'utente, automatica di SQL Server 2017 macchina Services (In-Database) con il linguaggio R aggiunto.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
```

Si noti il flag necessari per R in SQL Server 2017:

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MR`
+ `IACCEPTROPENLICENSETERMS`.

### <a name="install-python-only"></a>Solo l'installazione di Python

Nell'esempio seguente viene illustrato come installare gli argomenti necessari per eseguire un invisibile all'utente, automatica di SQL Server 2017 macchina Services (In-Database) con il linguaggio Python aggiunto.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

Si noti il flag necessari per Python in SQL Server 2017:

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MPY`
+ `IACCEPTPYTHONOPENLICENSETERMS`

### <a name="install-both-r-and-python-on-a-named-instance"></a>Installare R sia Python in un'istanza denominata

Nell'esempio seguente mostra gli argomenti necessari per eseguire un invisibile all'utente, automatica installazione di SQL Server 2017 macchina Services (In-Database) in un'istanza denominata. Vengono aggiunti linguaggi sia R e Python.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER.ServerName /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

## <a name="OldInstall"></a> Installazione della riga di comando per SQL Server 2016
 
Nell'esempio seguente viene illustrato come installare gli argomenti necessari per eseguire un invisibile all'utente, automatica di SQL Server 2016 con il linguaggio R aggiunto.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
```

Si noti il flag necessari per 2016 R Services:

+ `ADVANCEDANALYTICS`
+ `IACCEPTROPENLICENSETERMS`

## <a name = "bkmk_PostInstall"></a>Passaggi aggiuntivi dopo l'installazione

Al termine dell'installazione di SQL Server, indipendentemente da quale versione è installata, è necessario eseguire i passaggi seguenti. Machine learning funzionalità non sono abilitate per impostazione predefinita e deve essere abilitata in modo esplicito.

1.  Al termine dell'installazione, aprire una nuova **Query** finestra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ed eseguire il comando seguente per abilitare la funzionalità.
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  È necessario abilitare esplicitamente la funzionalità e riconfigurare; in caso contrario, non sarà possibile richiamare gli script esterni, anche se la funzionalità è stata installata.
  
2.  Riavviare il servizio SQL Server per l'istanza riconfigurato. In questo modo verrà riavviato automaticamente la correlate [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] anche servizio.

> [!IMPORTANT]
> 
> Se è presente una configurazione di sicurezza personalizzato o se si utilizzerà SQL Server come un contesto di calcolo durante l'esecuzione di codice Python o R da un client remoto, potrebbero essere necessari alcuni passaggi aggiuntivi. 
> 
> Per altre informazioni, vedere [domande frequenti sull'aggiornamento e l'installazione](../../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md).
