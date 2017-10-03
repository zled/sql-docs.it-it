---
title: Installare Microsoft R Server dalla riga di comando | Microsoft Docs
ms.custom: 
ms.date: 04/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: 4
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: b9f6ceba4d3609a7e7ff816d31446a77c4fea64c
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="install-microsoft-r-server-from-the-command-line"></a>Installare Microsoft R Server dalla riga di comando
    
In questo argomento viene descritto come utilizzare gli argomenti della riga di comando di SQL Server per installare Microsoft R Server in SQL Server 2016 o Machine Learning Server (Standalone) in SQL Server 2017. 

> [!NOTE]
È anche possibile installare Microsoft R Server utilizzando un programma di installazione di Windows separato. Per ulteriori informazioni, vedere [installare R Server 9.0.1 per Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows). 

## <a name="prerequisites"></a>Prerequisiti

Questo metodo di installazione è necessario sapere come eseguire un'installazione da riga di comando di SQL Server e si ha familiarità con i relativi argomenti di scripting.

- Per un'installazione**automatica** è necessario specificare il percorso dell'utilità di installazione e usare gli argomenti per indicare le funzionalità da installare. 
- Per un'installazione **non interattiva** , specificare gli stessi argomenti e aggiungere l'opzione **/q** . In questo modo non vengono visualizzati messaggi di richiesta e non è necessaria alcuna interazione. Se tuttavia viene omesso uno qualsiasi degli argomenti obbligatori, l'installazione non riesce.

Per altre informazioni, vedere [Installare SQL Server 2016 dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).

## <a name="sql-server-2017-microsoft-machine-learning-server-standalone"></a>SQL Server 2017: Microsoft Machine Learning Server (Standalone)

Eseguire il comando seguente da un prompt dei comandi con privilegi elevati per installare solo Microsoft Learning Server computer (autonomo) e i relativi prerequisiti.  L'esempio mostra gli argomenti utilizzati per installare R.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MR  /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS 
```

Per visualizzare lo stato e i messaggi di richiesta, rimuovere l'argomento _/q_.

- **FUNZIONALITÀ = SQL_SHARED_MR** ottiene solo i componenti Server di Machine Learning. Sono inclusi tutti i prerequisiti, che vengono installati automaticamente per impostazione predefinita.
- **SQL_INST_MR** è necessaria per supportare installl per il linguaggio R.
- **SQL_INST_MPY** è necessario per installare il supporto per Python.
- **IACCEPTROPENLICENSETERMS** indica che si sono accettate le condizioni di licenza per l'uso dei componenti R open source.
- **IACCEPTPYTHONLICENSETERMS** indica che si abbia accettato le condizioni di licenza per l'utilizzo dei componenti di Python.
- **IACCEPTSQLSERVERLICENSETERMS** è necessario per eseguire l'Installazione guidata.

**Note**

1. Poiché le condizioni di licenza di SQL Server, è necessario, l'argomento di funzionalità.
2. Specificare almeno una lingua, con il flag di contratto di licenza.
3. È possibile installare una lingua, o R e Python, ma è necessaria per ogni una licenza separata.

## <a name="sql-server-2016-microsoft-r-server-standalone"></a>SQL Server 2016: Microsoft R Server (Standalone)

Eseguire il comando seguente da un prompt dei comandi con privilegi elevati per installare solo Microsoft R Server (Standalone) e i relativi prerequisiti.  L'esempio mostra gli argomenti utilizzati con l'installazione di SQL Server 2016.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

## <a name="offline-installation"></a>Installazione offline

Se si installa Machine Learning Server o Microsoft R Server (Standalone) in un computer che non dispone di alcun accesso a Internet, è necessario scaricare i componenti R in anticipo e copiarli in una cartella locale. Per i collegamenti di download, vedere [Installazione dei componenti R senza accesso a Internet](../r/installing-ml-components-without-internet-access.md).

## <a name="what-is-installed"></a>Elementi installati

Al termine dell'installazione, è possibile esaminare il file di configurazione creato dal programma di installazione di SQL Server, insieme a un riepilogo delle azioni di installazione.

Per impostazione predefinita, tutti del programma di installazione dei riepiloghi e i registri per SQL Server e le funzionalità correlate vengono create nelle cartelle seguenti:

- SQL Server 2016:`C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log`
- SQL Server 2017:`C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log`

Per ogni funzionalità installata viene creata una sottocartella separata.

Per configurare un'altra istanza di Microsoft R Server con gli stessi parametri, è possibile utilizzare nuovamente il file di configurazione che viene creato durante l'installazione. Per ulteriori informazioni, vedere [installare SQL Server tramite un File di configurazione](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)


## <a name="customize-your-r-environment"></a>Personalizzare l'ambiente R

Dopo l'installazione, è possibile installare altri pacchetti R. Per altre informazioni, vedere [Installazione e gestione dei pacchetti R](../r/install-additional-r-packages-on-sql-server.md).

> [!IMPORTANT]
> Se si prevede di eseguire codice R in SQL Server, assicurarsi di installare gli stessi pacchetti nel computer che verrà usata per lo sviluppo della soluzione e l'istanza di SQL Server in cui si eseguire oppure distribuire la soluzione.

Dopo aver installato Servizi di Machine Learning per R (In-Database), è possibile utilizzare il programma di installazione di Windows separato per aggiornare la versione di R che è associata a un'istanza di SQL Server specificata. Per ulteriori informazioni, vedere [SqlBindR utilizzare per eseguire l'aggiornamento R](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).



