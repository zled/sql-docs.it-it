---
title: Pianificare i pacchetti SSIS in Linux con cron | Documenti Microsoft
description: In questo articolo viene descritto come pianificare i pacchetti di SQL Server Integration Services (SSIS) in Linux con il servizio cron.
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
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
ms.workload: Inactive
ms.openlocfilehash: 005757c0a1b1f4309201fc7b7c63987f4ff3bcb8
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>Esecuzione in Linux con cron del pacchetto di pianificazione di SQL Server Integration Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Quando si esegue SQL Server Integration Services (SSIS) e SQL Server in Windows, è possibile automatizzare l'esecuzione di pacchetti SSIS utilizzando SQL Server Agent. Quando si esegue SQL Server e SSIS in Linux, tuttavia, l'utilità di SQL Server Agent non è disponibile per pianificare i processi in Linux. È invece necessario utilizzare il servizio cron, che è ampiamente utilizzato su piattaforme Linux per automatizzare l'esecuzione del pacchetto.

In questo articolo vengono forniti esempi che illustrano come automatizzare l'esecuzione di pacchetti SSIS. Gli esempi sono scritti per l'esecuzione in Red Hat Enterprise. Il codice è simile per altre distribuzioni Linux, ad esempio Ubuntu.

## <a name="prerequisites"></a>Prerequisiti

Prima di utilizzare il servizio cron per eseguire i processi, verificare se è in esecuzione nel computer in uso.

Per controllare lo stato del servizio cron, utilizzare il comando seguente: `systemctl status crond.service`.

Se il servizio non è attivo (vale a dire, non è in esecuzione), rivolgersi all'amministratore per installare e configurare il servizio cron correttamente.

## <a name="create-jobs"></a>Creazione di processi

Un processo cron è un'attività che è possibile configurare per l'esecuzione a intervalli regolari a un intervallo specificato. Il processo può essere semplice come un comando che in genere digitare direttamente nella console o eseguire come script della shell.

Per una gestione semplificata e scopi di manutenzione, è consigliabile inserire i comandi di esecuzione del pacchetto in uno script che contiene un nome descrittivo.

Di seguito è riportato un esempio di uno script della shell semplice per l'esecuzione di un pacchetto. Contiene solo un singolo comando, ma è possibile aggiungere più comandi in base alle esigenze.

```bash
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Pianificare i processi con il servizio cron

Dopo aver definito i processi, è possibile pianificare vengano eseguiti automaticamente tramite il servizio cron.

Per aggiungere il processo per cron per l'esecuzione, aggiungere il processo nel file crontab. Per aprire il file crontab in un editor che consente di aggiungere o aggiornare il processo, usare il comando seguente: `crontab -e`.

Per pianificare il processo descritto in precedenza per l'esecuzione ogni giorno alle ore 2:10, aggiungere la riga seguente al file crontab:

```
# run <SSIS package name> at 2:10 AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

Salvare il file crontab e quindi chiudere l'editor.

Per comprendere il formato del comando di esempio, esaminare le informazioni nella sezione seguente.
 
## <a name="format-of-a-crontab-file"></a>Formato di un file crontab

L'immagine seguente mostra la descrizione del formato della riga di processo che viene aggiunto al file crontab.

![Formato descrizione della voce nel file crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

Per ottenere una descrizione più dettagliata del formato di file crontab, utilizzare il comando seguente: `man 5 crontab`.

Ecco un esempio parziale dell'output che consente di illustrare nell'esempio riportato in questo articolo:

![Descrizione parziale del formato crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)
