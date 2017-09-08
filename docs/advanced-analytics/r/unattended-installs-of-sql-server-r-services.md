---
title: Installazione automatica di Machine Learning Services | Documenti Microsoft
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
caps.latest.revision: 18
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: babb74aa866404853cfef83e1d30159354f385e7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="unattended-installation-of-machine-learning-services-in-database"></a>Installazione automatica di Machine Learning Services (In-Database)

In questo argomento viene descritto come utilizzare gli argomenti della riga di comando con l'installazione di SQL Server per installare l'apprendimento in un'istanza del motore di database, in modalità non interattiva. In un'installazione automatica, non utilizzare le funzionalità interattive dell'installazione guidata e deve fornire tutti gli argomenti necessari per completare l'installazione, incluse le licenze contratti per SQL Server e per i componenti di machine learning.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services (In-Database)

> [!IMPORTANT]
> 
> In SQL Server 2016 e SQL Server 2017, sono necessari passaggi aggiuntivi al termine dell'installazione per abilitare la funzionalità. Queste includono una riconfigurazione e riavvio dell'istanza. Assicurarsi di esaminare tutti i passaggi.

## <a name="prerequisites"></a>Prerequisiti

+ È necessario installare il motore di database in ogni istanza in cui verrà utilizzato l'apprendimento.

+ Se il computer non ha accesso a Internet, assicurarsi di installare i programmi di installazione di machine learning in anticipo i componenti. Per i percorsi di download, vedere [l'installazione dei componenti di machine learning senza accesso a Internet](../../advanced-analytics/r/installing-ml-components-without-internet-access.md).

+ Sono disponibili nuove licenze parametri relativi ai componenti di origine aperti per R e Python. È necessario accettare le condizioni di licenza con un argomento separato per ogni lingua da installare. Se questo parametro non viene incluso nella riga di comando, l'installazione non riesce.

+ Per completare l'installazione senza la necessità di rispondere ai prompt, assicurarsi di aver identificato tutti gli argomenti obbligatori, incluse quelle per le licenze e ad altre funzionalità che si potrebbero voler installare.

> [!NOTE] 
> Nelle prime versioni, è necessaria la modalità di sicurezza mista che supporta gli account di accesso SQL. Tuttavia, è possibile abilitare l'autenticazione modalità mista supportare lo sviluppo di soluzioni dagli esperti di dati utilizzando un account di accesso SQL.

## <a name="bkmk_NewInstall"></a>Installazione automatica di servizi di Machine Learning con R

Nell'esempio seguente il **minimo** installare le funzionalità necessarie per specificare nella riga di comando quando si esegue un invisibile all'utente, automatica di SQL Server 2017 macchina Services (In-Database).

1. Aprire un prompt dei comandi con privilegi elevati ed eseguire il comando seguente:

    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
    ```
    
    Si noti il flag necessari per R in SQL Server 2017: `ADVANCEDANALYTICS`, `SQL_INST_MR`, e `IACCEPTROPENLICENSETERMS`.
2. Riavviare il server.
3. Eseguire i passaggi di configurazione post-installazione, come descritto in [in questa sezione](#bkmk_PostInstall). Un altro riavvio dei servizi di SQL Server sono necessario.

## <a name="OldInstall"></a>Installazione automatica di R Services (In-Database)
 
 Nell'esempio seguente il **minimo** installare le funzionalità necessarie per specificare nella riga di comando quando si esegue un invisibile all'utente, automatica di SQL Server 2016 R Services.

1. Aprire un prompt dei comandi con privilegi elevati ed eseguire il comando seguente:

    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
    ```
    Si noti il flag necessari per i servizi R 2016: `ADVANCEDANALYTICS` e `IACCEPTROPENLICENSETERMS`.
2. Riavviare il server.
3. Eseguire i passaggi di configurazione post-installazione, come descritto in [in questa sezione](#bkmk_PostInstall). Un altro riavvio dei servizi di SQL Server sono necessario.

## <a name = "bkmk_PostInstall"></a>Passaggi aggiuntivi dopo l'installazione

1.  Al termine dell'installazione, aprire una nuova **Query** finestra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ed eseguire il comando seguente per abilitare la funzionalità.
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  È necessario abilitare esplicitamente la funzionalità e riconfigurare; in caso contrario, non sarà possibile richiamare gli script esterni, anche se la funzionalità è stata installata.
  
2.  Riavviare il servizio SQL Server per l'istanza riconfigurato. In questo modo verrà riavviato automaticamente correlata [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] anche servizio.

3. Potrebbero essere necessari alcuni passaggi aggiuntivi in presenza di una configurazione di sicurezza personalizzata o se si intende usare SQL Server per supportare contesti di calcolo remoto. Per altre informazioni, vedere [Domande frequenti sull'installazione e sull'aggiornamento](../../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md).

