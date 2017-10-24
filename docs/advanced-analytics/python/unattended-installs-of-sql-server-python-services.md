---
title: Installazione automatica di Python Machine Learning Services (In-Database) | Documenti Microsoft
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b9156a3dc9dec21187eec8dc0b5a44059fb5e31
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="unattended-installation-of-python-machine-learning-services-in-database"></a>Installazione automatica di Python Machine Learning Services (In-Database)

In questo argomento viene descritto come utilizzare gli argomenti della riga di comando di installazione di SQL Server 2017 per installare il motore di database di SQL Server con servizi di Machine Learning e Python, utilizzando la modalità non interattiva.

> [!NOTE]
> Non dimenticare di includere gli argomenti della riga di comando per i contratti di licenza, uno per Python e uno per SQL Server.

## <a name="prerequisites"></a>Prerequisiti

Prima di avviare il processo di installazione, tenere presenti questi requisiti:

+ Il servizio di Python non può essere installato in modo indipendente dal motore di database di SQL Server 2017. È necessario includere la funzionalità motore di database SQL.
+ Se si esegue un'installazione offline, è necessario scaricare i componenti necessari di Python in anticipo e copiarli in una cartella locale. Per i percorsi di download, vedere [installazione dei componenti di apprendimento computer senza accesso a Internet](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md).
+ È disponibile un nuovo parametro */IACCEPTPYTHONLICENSETERMS*, indicante che si abbia accettato le condizioni di licenza per usare i componenti di Python forniti da Analitica di continuità. Se questo parametro non viene incluso nella riga di comando, l'installazione non riesce.
+ Per completare l'installazione senza la necessità di rispondere ai prompt, assicurarsi di aver identificato tutti gli argomenti obbligatori, inclusi quelli per Python e delle licenze di SQL Server e ad altre funzionalità che si potrebbero voler installare.
+  In alcune versioni non definitive di SQL Server 2016, è necessaria l'autenticazione modalità mista. Non è più necessario, anche se potrebbe essere utile negli scenari di sviluppo e testing delle soluzioni in modalità remota utilizzando gli account di accesso SQL in cui gli esperti di dati.

## <a name="perform-an-unattended-installation-of-python-machine-learning-services-in-database"></a>Eseguire un'installazione automatica di Python Machine Learning Services (In-Database)

Nell'esempio seguente il **minimo** necessarie le funzionalità da specificare nella riga di comando quando si esegue un'installazione invisibile all'utente di Python e il motore di database nell'istanza predefinita.

> [!NOTE]
> Questa funzionalità richiede SQL Server 2017. Python è supportata nelle versioni precedenti di SQL Server.

1. Aprire un prompt dei comandi con privilegi elevati ed eseguire il comando seguente:

    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONLICENSETERMS
    ```

    > [!NOTE]
    > 
    > Esistono nuovi flag di installazione per Python: `SQL_INST_MPY` e`IACCEPTPYTHONLICENSETERMS`

2. Riavviare il server come indicato.
3. Eseguire i passaggi di configurazione post-installazione, come descritto in [in questa sezione](#bkmk_PostInstall). Un altro riavvio dei servizi di SQL Server sono necessario.

## <a name = "bkmk_PostInstall"></a>Passaggi successivi all'installazione

1.  Al termine dell'installazione, aprire una nuova **Query** finestra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ed eseguire il comando seguente per abilitare la funzionalità.

    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  È necessario abilitare esplicitamente la funzionalità e riconfigurare; in caso contrario, non sarà possibile richiamare gli script esterni, anche se la funzionalità è stata installata.
  
3.  Riavviare il servizio SQL Server per l'istanza riconfigurato. In questo modo verrà riavviato automaticamente correlata [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] anche servizio.

3. Potrebbero essere necessari alcuni passaggi aggiuntivi in presenza di una configurazione di sicurezza personalizzata o se si intende usare SQL Server per supportare contesti di calcolo remoto. Per ulteriori informazioni, vedere [risoluzione dei problemi di installazione di machine learning](../machine-learning-troubleshooting-faq.md).

