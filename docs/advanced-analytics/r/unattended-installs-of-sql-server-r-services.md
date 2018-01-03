---
title: Installazione automatica di Machine Learning Services | Documenti Microsoft
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: fdd28279b99f0dd39a0b971412d1252feb978413
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="unattended-installation-of-machine-learning-services-in-database"></a>Installazione automatica di Machine Learning Services (In-Database)

In questo articolo viene descritto come utilizzare gli argomenti della riga di comando con l'installazione di SQL Server per l'installazione di machine learning componenti.

Per l'installazione automatica, si intende non utilizzare le funzionalità interattive dell'installazione guidata e invece fornire tutti gli argomenti necessari per completare l'installazione, incluse le licenze contratti per SQL Server e per i componenti di machine learning in un riga di comando o come parte di uno script, in genere in modalità non interattiva.

+ [SQL Server 2016 R Services](#bkmk_OldInstall)
+ [SQL Server 2017 Machine Learning Services](#bkmk_NewInstall) con R o Python
+ [Microsoft R Server o Server di Machine Learning](../r/install-microsoft-r-server-from-the-command-line.md)

**Si applica a: SQL Server 2017 Machine Learning Services (In-Database), SQL Server 2016 R Services**

## <a name="prerequisites"></a>Prerequisites

+ È necessario installare il motore di database in ogni istanza in cui verrà utilizzato l'apprendimento.

+ Se il computer non ha accesso a Internet, assicurarsi di scaricare i programmi di installazione di machine learning in anticipo i componenti. Vedere [l'installazione dei componenti di machine learning senza accesso a Internet](../r/installing-ml-components-without-internet-access.md).

+ Esistono separate le licenze di parametri per ognuno dei componenti di origine aperti di R e Python. SQL Server 2016 supporta solo R; SQL Server 2017 supporta R e Python. È necessario accettare le condizioni di licenza per ogni lingua da installare. Il programma di installazione ha esito negativo se non si include questo parametro nella riga di comando.

+ Per completare l'installazione senza la necessità di rispondere ai prompt, assicurarsi di aver identificato tutti gli argomenti obbligatori, incluse quelle per le licenze e ad altre funzionalità che si potrebbero voler installare.

+ Il **Mixed** modalità di sicurezza che supporta gli account di accesso SQL era richiesto nelle prime versioni. Anche se non è più necessario, è possibile abilitare l'autenticazione modalità mista supportare lo sviluppo di soluzioni dagli esperti di dati che utilizzano un account di accesso SQL.

> [!IMPORTANT]
> 
> Al termine dell'installazione per abilitare la funzionalità, sono necessari passaggi aggiuntivi. Queste includono una riconfigurazione e riavvio dell'istanza. Assicurarsi di esaminare tutti gli elementi nella sezione [passaggi di post-installazione] (#bkmk_PostInstall) per determinare le azioni necessario al termine dell'installazione.

## <a name="bkmk_NewInstall"></a>Installazione della riga di comando per SQL Server 2017

Di seguito sono riportati esempi di **minimo** funzionalità necessarie.

> [!IMPORTANT]
> Assicurarsi di eseguire tutti i comandi da un prompt dei comandi con privilegi elevati.
> 
> Al termine dell'installazione, sono necessari alcuni passaggi aggiuntivi. Vedere [in questa sezione](#bkmk_PostInstall). 
> Un altro riavvio dei servizi di SQL Server sono necessario al termine della configurazione.

### <a name="install-r-only"></a>Solo l'installazione di R

L'esempio seguente mostra gli argomenti necessari per eseguire un invisibile all'utente, automatica installazione di SQL Server 2017 macchina Services (In-Database) con il linguaggio R aggiunto.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
```

Si noti il flag necessari per R in SQL Server 2017:

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MR`
+ `IACCEPTROPENLICENSETERMS`(Indici per tabelle con ottimizzazione per la memoria).

### <a name="install-python-only"></a>Solo l'installazione di Python

L'esempio seguente mostra gli argomenti necessari per eseguire un invisibile all'utente, automatica installazione di SQL Server 2017 macchina Services (In-Database) con il linguaggio Python aggiunto.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

Si noti il flag necessari per Python in SQL Server 2017:

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MPY`
+ `IACCEPTPYTHONOPENLICENSETERMS`

### <a name="install-both-r-and-python-on-a-named-instance"></a>Installare R sia Python in un'istanza denominata

Nell'esempio seguente visualizza gli argomenti necessari per eseguire un invisibile all'utente, automatica di installazione di SQL Server 2017 macchina Services (In-Database) in un'istanza denominata. Vengono aggiunti i linguaggi sia R e Python.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER.ServerName /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

## <a name="OldInstall"></a>Installazione della riga di comando per SQL Server 2016
 
L'esempio seguente mostra gli argomenti necessari per eseguire un invisibile all'utente, automatica di installazione di SQL Server 2016 con il linguaggio R aggiunto.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
```

Si noti il flag necessari per 2016 R Services:

+ `ADVANCEDANALYTICS`
+ `IACCEPTROPENLICENSETERMS`

## <a name = "bkmk_PostInstall"></a>Passaggi aggiuntivi dopo l'installazione

Al termine dell'installazione di SQL Server, indipendentemente dal quale versione è installata, è necessario eseguire i passaggi seguenti. funzionalità di Machine learning non sono abilitate per impostazione predefinita e deve essere abilitata in modo esplicito.

1.  Al termine dell'installazione, aprire una nuova **Query** finestra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ed eseguire il comando seguente per abilitare la funzionalità.
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  È necessario abilitare esplicitamente la funzionalità e riconfigurare; in caso contrario, non sarà possibile richiamare gli script esterni, anche se la funzionalità è stata installata.
  
2.  Riavviare il servizio SQL Server per l'istanza riconfigurato. In questo modo verrà riavviato automaticamente correlata [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] anche servizio.

> [!IMPORTANT]
> 
> Se si dispone di una configurazione di sicurezza personalizzato o se si utilizzerà il Server SQL come contesto di calcolo durante l'esecuzione di codice R o Python da un client remoto, potrebbero essere necessari alcuni passaggi aggiuntivi. 
> 
> Per ulteriori informazioni, vedere [domande frequenti sull'installazione e aggiornamento](../../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md).
