---
title: Pianificare i pacchetti SSIS in Linux con cron | Documenti Microsoft
description: In questo articolo viene illustrato come pianificare i pacchetti di SQL Server Integration Services in Linux con il servizio cron.
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.date: 09/26/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: integration-services
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 31d5fb63a9c2a4d8825aa39c6fa7e3377ddc8d91
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>Esecuzione in Linux con cron del pacchetto di pianificazione di SQL Server Integration Services

Quando si esegue SQL Server Integration Services (SSIS) e SQL Server in Windows, è possibile automatizzare l'esecuzione di pacchetti SSIS utilizzando SQL Server Agent. Quando si esegue SQL Server e SSIS in Linux, tuttavia, l'utilità di SQL Server Agent non è disponibile per pianificare i processi in Linux. Usare invece **Cron** servizio ampiamente utilizzato su piattaforme Linux per automatizzare l'esecuzione del pacchetto.

In questo articolo vengono forniti esempi che illustrano come automatizzare l'esecuzione di pacchetti SSIS. Gli esempi sono stati scritti per l'esecuzione in Red Hat Enterprise. Il codice è simile per altre distribuzioni Linux come Ubuntu.

## <a name="prerequisites"></a>Prerequisiti

Prima di utilizzare il servizio Cron per eseguire i processi, è necessario controllare se il servizio Cron è in esecuzione nel computer in uso.

Utilizza il seguente comando per controllare lo stato del servizio Cron.

`systemctl status crond.service`

Se il servizio non è attivo (vale a dire, non in esecuzione), rivolgersi all'amministratore per installare e configurare il servizio Cron correttamente.

## <a name="create-jobs"></a>Crea processi

Un processo Cron è un'attività che è possibile configurare per l'esecuzione a intervalli regolari a un intervallo specificato. Il processo può essere semplice come un comando che in genere digitare direttamente nella console o eseguire come script della shell.

Per una gestione semplificata e scopi di manutenzione, è consigliabile per inserire i comandi di esecuzione del pacchetto in uno script con un nome descrittivo.

Di seguito è riportato un esempio semplice di uno script della shell che contiene solo singolo comando per eseguire un pacchetto. È possibile aggiungere altri comandi come richiesto.

```
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Pianificare i processi con il servizio Cron

Dopo aver definito i processi, è possibile pianificare vengano eseguiti automaticamente tramite il servizio Cron.

Per aggiungere il processo per Cron per l'esecuzione, è necessario aggiungere il processo nel `crontab` file. Per aprire la `crontab` file in un editor che consente di aggiungere o aggiornare il processo, usare il comando seguente:

`crontab -e`

Per pianificare il processo descritto in precedenza per l'esecuzione ogni giorno alle ore 2:10, aggiungere la seguente riga per il `crontab` file:

```
# run SSIS package Name at 2:10AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

Salvare il `crontab` file e chiudere l'editor.

Per comprendere il formato del comando di esempio, esaminare le informazioni nella sezione seguente.
 
## <a name="format-of-a-crontab-file"></a>Formato di un file Crontab

La figura seguente mostra la descrizione del formato della riga di processo aggiunta per il `crontab` file.

![Formato descrizione della voce nel file crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

Per ottenere una descrizione più dettagliata del `crontab` formato di file, utilizzare il comando seguente:

`man 5 crontab`

Ecco un esempio parziale dell'output che consente di illustrare nell'esempio riportato in questo articolo:

![Descrizione parziale del formato crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)

