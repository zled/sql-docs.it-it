---
title: Installazione dalla riga di comando di Machine Learning Server (Standalone) o Microsoft R Server (Standalone) | Documenti Microsoft
ms.custom: 
ms.date: 10/31/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: "4"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 400f743bfbb065a5e271b5ff335d0896bb2ac3ef
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="install-machine-learning-server-standalone-or-microsoft-r-server-standalone-from-the-command-line"></a>Installazione dalla riga di comando di Machine Learning Server (Standalone) o Microsoft R Server (Standalone)

In questo articolo viene descritto come utilizzare gli argomenti della riga di comando di SQL Server per installare le seguenti funzionalità di SQL Server tramite la riga di comando:

+ [In SQL Server 2017 di Machine Learning Server (Standalone)](#bkmk_mls2017) 
+ [Microsoft R Server (Standalone), in SQL Server 2016](#bkmk_mrs2016)

Un **automatica** installazione è necessario specificare il percorso dell'utilità di installazione e utilizzare gli argomenti per indicare le funzionalità da installare.

Per un'installazione **non interattiva** , specificare gli stessi argomenti e aggiungere l'opzione **/q** . Nessuna richiesta viene fornita e l'intervento del non è obbligatorio. Tuttavia, il programma di installazione non riesce se vengono omessi gli argomenti richiesti.

## <a name="prerequisites"></a>Prerequisiti

È necessario sapere eseguire un'installazione da riga di comando di SQL Server e acquisire familiarità con i relativi argomenti di scripting.

Per ulteriori informazioni, vedere [installazione di SQL Server dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).

Se si installa Machine Learning Server o Microsoft R Server (Standalone) in un computer che non dispone di alcun accesso a Internet, è necessario scaricare i componenti necessari di R (o Python) in anticipo e copiarli in una cartella locale. Per i percorsi di download, vedere [l'installazione dei componenti di machine learning senza accesso a internet](installing-ml-components-without-internet-access.md).


## <a name="bkmk_mls2017"></a>Installare Microsoft Machine Learning Server (Standalone)

**Si applica a: SQL Server 2017**

Eseguire il comando seguente da un prompt dei comandi con privilegi elevati per installare solo Machine Learning Server (Standalone) e i relativi prerequisiti.

+ Poiché le condizioni di licenza di SQL Server, è necessario, l'argomento di funzionalità.
+ È possibile installare una lingua, o R e Python, ma è necessaria per ogni una licenza separata.

Questo esempio mostra gli argomenti utilizzati per installare R.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MR  /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

Questo esempio mostra gli argomenti utilizzati per installare Python.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MPY  /IACCEPTPYTHONOPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

+ Per visualizzare lo stato e i messaggi di richiesta, rimuovere l'argomento _/q_.
+ Se si utilizza l'argomento **funzionalità = SQL_SHARED_MR**, solo i componenti Server di Machine Learning sono installati con R né Python. Questa installazione include tutti i prerequisiti vengono installati automaticamente per impostazione predefinita. Tuttavia, si consiglia di aggiungere almeno una lingua durante l'installazione per la prima volta.
+ Aggiungere **SQL_INST_MR** per installare il supporto per R.
+ Aggiungere **SQL_INST_MPY** per installare il supporto per Python.
+ **IACCEPTROPENLICENSETERMS** indica che si sono accettate le condizioni di licenza per l'uso dei componenti R open source.
+ **IACCEPTPYTHONLICENSETERMS** indica che si abbia accettato le condizioni di licenza per l'utilizzo dei componenti di Python.
+ **IACCEPTSQLSERVERLICENSETERMS** è necessario per eseguire l'Installazione guidata.


## <a name="bkmk_mrs2016"></a> Installare Microsoft R Server (Standalone)

**Si applica a: SQL Server 2016**

Eseguire il comando seguente da un prompt dei comandi con privilegi elevati per installare **solo** Microsoft R Server (Standalone) e i relativi prerequisiti. 

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

> [!TIP]
> È consigliabile non installare questa nello stesso computer che ospita un'istanza di SQL Server R Services.

## <a name="post-installation-tasks"></a>Attività successive all'installazione

Per configurare un'altra istanza di Microsoft R Server con gli stessi parametri, è possibile utilizzare nuovamente il file di configurazione che viene creato durante l'installazione. Per ulteriori informazioni, vedere [installazione di SQL Server utilizzando un file di configurazione](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md).

### <a name="review-installed-components"></a>Componenti installato di revisione

Al termine dell'installazione, è possibile esaminare il file di configurazione creato dal programma di installazione di SQL Server, insieme a un riepilogo delle azioni di installazione.

Per impostazione predefinita, tutti del programma di installazione dei riepiloghi e i registri per SQL Server e le funzionalità correlate vengono create nelle cartelle seguenti:

+ SQL Server 2017:`C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log`
+ SQL Server 2016:`C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log`

Viene creata una sottocartella di separato per ogni funzionalità che è stato installato.

### <a name="customize-the-r-or-python-environment"></a>Personalizzare l'ambiente R o Python

Dopo l'installazione, è possibile installare altri pacchetti R o Python. Il processo è leggermente diversa a seconda se si utilizza SQL Server 2016 o SQL Server 2017.

In SQl Server 2017, è possibile installare e gestire i pacchetti R tramite T-SQL. Per ulteriori informazioni, vedere [installazione e la gestione dei pacchetti R](../r/install-additional-r-packages-on-sql-server.md).

Per Python e in SQL Server 2016, l'amministratore deve installare eventuali librerie aggiuntive che potrebbero essere necessarie.

> [!IMPORTANT]
> Se si prevede di eseguire codice R in SQL Server, assicurarsi di installare gli stessi pacchetti nel computer che verrà usata per lo sviluppo della soluzione e l'istanza di SQL Server in cui si eseguire oppure distribuire la soluzione.

### <a name="upgrading-r-server-or-sql-server-machine-learning"></a>L'aggiornamento di apprendimento R Server o SQL Server

Se non si intende utilizzare SQL Server, è possibile installare Microsoft R Server o Server di Machine Learning usando un programma di installazione di Windows separato. Per i percorsi di download e istruzioni, vedere i collegamenti:

+ [Installazione di Machine Learning Server per Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Installare R Server 9.0.1 per Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) 

Il programma di installazione di windows separato per Machine Learning Server può anche essere utilizzato per aggiornare di machine learning i componenti associati all'istanza.  Per ulteriori informazioni, vedere i collegamenti seguenti:

+ [Utilizzare SqlBindR per aggiornare R](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
