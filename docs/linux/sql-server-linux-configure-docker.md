---
title: Opzioni di configurazione per SQL Server 2017 in Docker | Documenti Microsoft
description: Esplorare i diversi modi di utilizzo e l'interazione con le immagini contenitore di SQL Server 2017 in Docker. Sono inclusi i dati persistenti, la copia dei file e risoluzione dei problemi.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: bdfc7ef9eb8048f1009f3c7f1a61533b6b620f37
ms.contentlocale: it-it
ms.lasthandoff: 10/02/2017

---
# <a name="configure-sql-server-2017-container-images-on-docker"></a>Configurare le immagini contenitore di SQL Server 2017 in Docker

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In questo argomento viene illustrato come configurare e utilizzare il [immagine contenitore mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) con Docker. Questa immagine è costituito da SQL Server in esecuzione in base a 16.04 Ubuntu Linux. E può essere utilizzato con il motore Docker 1.8 + in Linux o in Docker per Mac e Windows.

> [!NOTE]
> Questo argomento descrive in modo specifico utilizzando l'immagine mssql-server-linux. L'immagine di Windows non è coperto, ma sono disponibili ulteriori informazioni sul [pagina Hub Docker mssql-server-windows](https://hub.docker.com/r/microsoft/mssql-server-windows/).

## <a name="pull-and-run-the-container-image"></a>Effettuare il pull ed eseguire l'immagine del contenitore

Per effettuare il pull ed eseguire di immagine contenitore Docker per SQL Server 2017, seguire i prerequisiti e i passaggi nell'esercitazione introduttiva seguenti:

- [Eseguire l'immagine di SQL Server 2017 contenitore con Docker](quickstart-install-connect-docker.md)

In questo argomento configurazione fornisce aggiuntivi per la connessione e scenari di utilizzo nelle sezioni seguenti.

## <a name="connect-and-query"></a>Connettersi ed eseguire query

È possibile connettersi ed eseguire query di SQL Server in un contenitore dall'esterno del contenitore o dall'interno il contenitore. Le sezioni seguenti illustrano entrambi gli scenari. 

### <a name="tools-outside-the-container"></a>Strumenti di fuori del contenitore

È possibile connettersi all'istanza di SQL Server nel computer Docker da qualsiasi strumento esterno macOS, Windows o Linux che supporta le connessioni SQL. Alcuni strumenti comuni includono:

- [SQLCMD](sql-server-linux-setup-tools.md)
- [Codice di Visual Studio](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) in Windows](sql-server-linux-develop-use-ssms.md)

L'esempio seguente usa **sqlcmd** per connettersi a SQL Server in esecuzione in un contenitore Docker. L'indirizzo IP nella stringa di connessione è l'indirizzo IP del computer host in cui è in esecuzione il contenitore.

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

Se è eseguito il mapping di una porta dell'host che non è il valore predefinito **1433**, aggiungere tale porta alla stringa di connessione. Ad esempio, se è stato specificato `-p 1400:1433` nel `docker run` comando, quindi connettersi in modo esplicito da specificare porta 1400.

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>Strumenti all'interno del contenitore

A partire da SQL Server 2017 CTP 2.0, il [gli strumenti da riga di comando di SQL Server](sql-server-linux-setup-tools.md) sono inclusi nell'immagine contenitore. Se si collega all'immagine con un prompt dei comandi interattivi, è possibile eseguire gli strumenti in locale.

1. Utilizzare il `docker exec -it` comando per avviare una shell bash interattiva all'interno del contenitore in esecuzione. Nell'esempio seguente `e69e056c702d` è l'ID del contenitore.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Sempre necessario specificare l'id intero contenitore. È necessario solo specificare un numero di caratteri sufficiente per identificarla in modo univoco. In questo esempio, potrebbe pertanto essere sufficienti per utilizzare `e6` o `e69` anziché l'id completo.

2. Una volta all'interno del contenitore, la connessione in locale con sqlcmd. Si noti che sqlcmd non è inclusa nel percorso per impostazione predefinita, pertanto è necessario specificare il percorso completo.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. Al termine di sqlcmd, digitare `exit`.

4. Al termine di prompt dei comandi interattivo, digitare `exit`. Il contenitore continua a essere eseguito dopo la chiusura della shell bash interattivo.

## <a name="run-multiple-sql-server-containers"></a>Eseguire più contenitori di SQL Server

Docker offre un modo per eseguire più contenitori di SQL Server nello stesso computer host. Si tratta dell'approccio per scenari che richiedono più istanze di SQL Server nello stesso host. Ogni contenitore deve esporre stesso su una porta diversa.

Nell'esempio seguente vengono creati due contenitori di SQL Server e ne esegue il mapping alle porte **1401** e **1402** nel computer host.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d microsoft/mssql-server-linux:2017-latest
```

Sono ora presenti due istanze di SQL Server in esecuzione in contenitori separati. I client possono connettersi a ogni istanza di SQL Server utilizzando l'indirizzo IP dell'host Docker e il numero di porta per il contenitore.

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="persist"></a>I dati persistenti

Le modifiche alla configurazione di SQL Server e i file di database sono persistenti nel contenitore, anche se si riavvia il contenitore con `docker stop` e `docker start`. Tuttavia, se si rimuove il contenitore con `docker rm`, tutti gli elementi nel contenitore viene eliminato, tra cui SQL Server e i database. Nella sezione seguente viene illustrato come utilizzare **volumi di dati** per i file di database anche se i contenitori associati vengono eliminati.

> [!IMPORTANT]
> Per SQL Server, è fondamentale comprendere la persistenza dei dati in Docker. Oltre alle informazioni in questa sezione, vedere la documentazione di Docker in [come gestire i dati in contenitori di Docker](https://docs.docker.com/engine/tutorials/dockervolumes/).

### <a name="mount-a-host-directory-as-data-volume"></a>Montare una directory host come volume di dati

La prima opzione è per montare un volume di dati nel contenitore di una directory nell'host. A tale scopo, utilizzare il `docker run` comando con il `-v <host directory>:/var/opt/mssql` flag. In questo modo i dati da ripristinare tra le esecuzioni di contenitore.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

Questa tecnica consente anche di condividere e visualizzare i file nell'host all'esterno di Docker.

> [!IMPORTANT]
> Mapping del volume host per Docker su Mac con SQL Server in Linux immagine non è supportato in questo momento. Utilizzare contenitori di volumi di dati. Questa restrizione è specifica di `/var/opt/mssql` directory. Durante la lettura da una directory montata di funziona correttamente. Ad esempio, è possibile montare una directory host utilizzando – v su Mac e ripristinare un backup da un file con estensione bak che risiede nell'host.

### <a name="use-data-volume-containers"></a>Usare i contenitori di volumi di dati

La seconda opzione è utilizzare un contenitore di volumi di dati. È possibile creare un contenitore di volumi di dati specificando un nome di volume invece di una directory host con il `-v` parametro. L'esempio seguente crea un volume di dati condiviso denominato **sqlvolume**.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

> [!NOTE]
> Questa tecnica per la creazione di un volume di dati in modo implicito nel comando di esecuzione non funziona con le versioni precedenti di Docker. In tal caso, utilizzare i passaggi espliciti descritti nella documentazione di Docker, [creazione e montaggio di un contenitore di volumi di dati](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container).

Anche se si arresta e rimuovere questo contenitore, viene mantenuto il volume di dati. È possibile visualizzare con il `docker volume ls` comando.

```bash
docker volume ls
```

Se si crea quindi un altro contenitore con lo stesso nome di volume, il nuovo contenitore Usa gli stessi dati di SQL Server contenuti nel volume.

Per rimuovere un contenitore di volumi di dati, utilizzare il `docker volume rm` comando.

> [!WARNING]
> Se si elimina il contenitore del volume di dati, i dati di SQL Server nel contenitore sono *definitivamente* eliminato.

### <a name="backup-and-restore"></a>Backup e ripristino

Oltre a queste tecniche di contenitore, è inoltre possibile utilizzare backup di SQL Server standard e le tecniche di ripristino. È possibile utilizzare i file di backup per proteggere i dati o per spostare i dati in un'altra istanza di SQL Server. Per ulteriori informazioni, vedere [Backup e ripristino di database di SQL Server in Linux](sql-server-linux-backup-and-restore-database.md).

> [!WARNING]
> Se si creano i backup, assicurarsi di creare o copiare i file di backup di fuori del contenitore. Se viene rimosso il contenitore, in caso contrario, vengono eliminati anche i file di backup.

## <a name="execute-commands-in-a-container"></a>Eseguire i comandi in un contenitore

Se si dispone di un contenitore in esecuzione, è possibile eseguire i comandi all'interno del contenitore da un host terminal.

Per ottenere l'ID di contenitore eseguire:

```bash
docker ps
```

Per avviare un bash terminal nel contenitore eseguire:

```bash
docker exec -ti <Container ID> /bin/bash
```

È ora possibile eseguire comandi, come se sono in esecuzione in terminal all'interno del contenitore. Al termine, digitare `exit`. Questo viene chiuso nella sessione interattiva di comandi, ma il contenitore resta in esecuzione.

## <a name="copy-files-from-a-container"></a>Copiare i file da un contenitore

Per copiare un file dal contenitore, usare il comando seguente:

```bash
docker cp <Container ID>:<Container path> <host path>
```

**Esempio:**

```bash
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog /tmp/errorlog
```

```PowerShell
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog C:\Temp\errorlog
```

## <a name="copy-files-into-a-container"></a>Copiare i file in un contenitore

Per copiare un file nel contenitore, usare il comando seguente:

```bash
docker cp <Host path> <Container ID>:<Container path>
```

**Esempio:**

```bash
docker cp /tmp/mydb.mdf d6b75213ef80:/var/opt/mssql/data
```

```PowerShell
docker cp C:\Temp\mydb.mdf d6b75213ef80:/var/opt/mssql/data
```

## <a name="run-a-specific-sql-server-container-image"></a>Eseguire un'immagine di contenitore specifica di SQL Server

Esistono scenari in cui è possibile non usare l'immagine di contenitore più recente di SQL Server. Per eseguire un'immagine di contenitore specifica di SQL Server, attenersi alla procedura seguente:

1. Identificare il Docker **tag** per la versione che si desidera utilizzare. Per visualizzare i tag disponibili, vedere [pagina dell'hub Docker mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/).

1. Estrarre l'immagine del contenitore di SQL Server con il tag. Ad esempio, per eseguire il pull dell'immagine RC1, sostituire `<image_tag>` nel comando seguente con `rc1`.

   ```bash
   docker pull microsoft/mssql-server-linux:<image_tag>
   ```

1. Per eseguire un nuovo contenitore con l'immagine, specificare il nome di tag nel `docker run` comando. Il comando seguente, sostituire `<image_tag>` con la versione che si desidera eseguire.

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
   ```

Questa procedura consente inoltre effettuare il downgrade di un contenitore esistente. Ad esempio, è possibile ripristinare o effettuare il downgrade di un contenitore per la risoluzione dei problemi o test in esecuzione. Per effettuare il downgrade di un contenitore in esecuzione, è necessario utilizzare una tecnica di persistenza per la cartella di dati. La stessa procedura descritta nel [aggiornamento sezione](#upgrade), ma specificare il nome del tag della versione precedente, quando si esegue il nuovo contenitore.

> [!IMPORTANT]
> L'aggiornamento e il downgrade sono supportati solo tra RC1 e RC2 in questo momento.

## <a id="upgrade"></a>Aggiornamento di SQL Server nei contenitori

Per aggiornare l'immagine contenitore con Docker, identificare innanzitutto il tag per la versione di aggiornamento. Questa versione il pull dal Registro di sistema di `docker pull` comando:

```bash
docker pull microsoft/mssql-server-linux:<image_tag>
```

Aggiorna l'immagine di SQL Server per qualsiasi nuovi contenitori creati, ma non aggiorna SQL Server in tutti i contenitori in esecuzione. A tale scopo, è necessario creare un nuovo contenitore con l'immagine di contenitore più recente di SQL Server e la migrazione dei dati per il nuovo contenitore.

1. Assicurarsi che si utilizza uno del [tecniche di persistenza dei dati](#persist) per il contenitore di SQL Server esistente. Ciò consente di avviare un nuovo contenitore con gli stessi dati.

1. Arrestare il contenitore di SQL Server con il `docker stop` comando.

1. Creare un nuovo contenitore di SQL Server con `docker run` e specificare una directory host associato o un contenitore di volumi di dati. Assicurarsi di utilizzare il tag specifico per l'aggiornamento di SQL Server. Il nuovo contenitore utilizza ora una nuova versione di SQL Server con i dati di SQL Server esistenti.

   > [!IMPORTANT]
   > In questa fase di aggiornamento è supportato solo tra GA RC1 e RC2.

1. Verificare i database e i dati nel nuovo contenitore.

1. Facoltativamente, rimuovere il vecchio contenitore con `docker rm`.

## <a id="troubleshooting"></a>Risoluzione dei problemi

Le sezioni seguenti forniscono suggerimenti sulla risoluzione dei problemi per l'esecuzione di SQL Server nei contenitori.

### <a name="docker-command-errors"></a>Errori di comando di docker

Se si verificano errori per qualsiasi `docker` comandi, assicurarsi che il servizio docker sia in esecuzione e provare a eseguire con autorizzazioni elevate.

Ad esempio, in Linux, è possibile che venga visualizzato l'errore seguente durante l'esecuzione di `docker` comandi:

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Se questo errore si verifica in Linux, provare a eseguire gli stessi comandi preceduti da `sudo`. Se il problema persiste, verificare il servizio docker è in esecuzione e avviarlo, se necessario.

```bash
sudo systemctl status docker
sudo systemctl start docker
```

In Windows, verificare che si avvia PowerShell o prompt dei comandi come amministratore.

### <a name="sql-server-container-startup-errors"></a>Errori di avvio di SQL Server contenitore

Se il contenitore di SQL Server non viene eseguita, provare a eseguire i test seguenti:

- Se si verifica un errore, ad esempio **' non è riuscito a creare endpoint CONTAINER_NAME nel bridge di rete. Errore durante l'avvio proxy: associazione di ascolto tcp 0.0.0.0:1433: indirizzo già in uso.'** , quindi si sta tentando di eseguire il mapping a una porta è già in uso la porta 1433 del contenitore. Questa situazione può verificarsi se si esegue SQL Server in locale nel computer host. Può inoltre verificarsi se si avvia due contenitori di SQL Server e provare a eseguire il mapping di entrambi per la stessa porta host. In questo caso, utilizzare il `-p` parametro per il contenitore porta 1433 per eseguire il mapping a una porta di host diverso. Esempio: 

    ```bash
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d microsoft/mssql-server-linux:2017-latest`.
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d microsoft/mssql-server-linux:2017-latest`.
    ```

- Verificare se sono presenti eventuali messaggi di errore dal contenitore.

    ```bash
    docker logs e69e056c702d
    ```

- Assicurarsi di soddisfare i requisiti minimi di memoria e disco specificati nella [requisiti](#requirements) sezione di questo argomento.

- Se si utilizza qualsiasi software di gestione del contenitore, assicurarsi che supporta i processi di contenitore in esecuzione come radice. Il processo sqlservr nel contenitore viene eseguito come radice.

- Esaminare il [i log di errore e il programma di installazione di SQL Server](#errorlogs).

### <a name="enable-dump-captures"></a>Abilita le acquisizioni di dump

Se il processo di SQL Server non riesce all'interno del contenitore, è necessario creare un nuovo contenitore con **SYS_PTRACE** abilitato. Aggiunge la funzionalità di Linux per tracciare un processo, che è necessario per la creazione di un file di dump di un'eccezione. Il file di dump possa essere usato dal supporto tecnico per risolvere il problema. Il seguente comando docker run abilita questa funzionalità.

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
```

### <a name="sql-server-connection-failures"></a>Errori di connessione di SQL Server

Se non è possibile connettersi all'istanza di SQL Server in esecuzione nel contenitore, provare a eseguire i test seguenti:

- Assicurarsi che il contenitore di SQL Server sia in esecuzione esaminando il **stato** colonna del `docker ps -a` output. In caso contrario, utilizzare `docker start <Container ID>` per avviarlo.

- Se è stato eseguito il mapping a una porta non predefinita host (non 1433), assicurarsi che si specifica la porta nella stringa di connessione. È possibile visualizzare il mapping delle porte nel **porte** colonna il `docker ps -a` output. Il comando seguente, ad esempio, si connette sqlcmd in un contenitore in ascolto sulla porta 1401:

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- Se è stato utilizzato `docker run` con un volume di dati sottoposti a mapping esistente o un contenitore di volumi di dati, SQL Server ignora il valore di `MSSQL_SA_PASSWORD`. Al contrario, la password dell'utente dell'amministratore di sistema configurata in precedenza viene utilizzata dai dati di SQL Server nel volume di dati o il contenitore di volumi di dati. Verificare che si sta utilizzando la password associata ai dati che per l'associazione.

- Esaminare il [i log di errore e il programma di installazione di SQL Server](#errorlogs).

### <a name="sql-server-availability-groups"></a>Gruppi di disponibilità SQL Server

Se si utilizza Docker con gruppi di disponibilità di SQL Server, esistono due requisiti aggiuntivi.

- Associare la porta che viene utilizzata per la comunicazione di replica (impostazione predefinita 5022). Ad esempio, specificare `-p 5022:5022` come parte del `docker run` comando.

- Impostare in modo esplicito il nome host del contenitore con il `-h YOURHOSTNAME` parametro del `docker run` comando. Questo nome host viene utilizzato quando si configura il gruppo di disponibilità. Se non si specifica con `-h`, il valore predefinito è l'ID del contenitore.

### <a id="errorlogs"></a>Log di errore e il programma di installazione di SQL Server

È possibile esaminare il programma di installazione di SQL Server e il log degli errori **/var/opt/mssql/log**. Se il contenitore non è in esecuzione, avviare innanzitutto il contenitore. Utilizzare quindi un prompt dei comandi interattiva per esaminare i registri.

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

Dalla sessione bash all'interno del contenitore, eseguire i comandi seguenti:

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> Se è montato in una directory di host per **/var/opt/mssql** al momento della creazione del contenitore, è possibile invece esaminare il **log** sottodirectory nel percorso mappato nell'host.

## <a name="next-steps"></a>Passaggi successivi

Introduzione a SQL Server 2017 le immagini contenitore Docker attraverso il [esercitazione introduttiva](quickstart-install-connect-docker.md).

Vedere anche il [repository GitHub mssql docker](https://github.com/Microsoft/mssql-docker) per le risorse, commenti e suggerimenti e problemi noti.

