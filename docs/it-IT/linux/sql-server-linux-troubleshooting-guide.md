---
title: Risolvere i problemi relativi a SQL Server in Linux | Documenti Microsoft
description: Vengono forniti suggerimenti sulla risoluzione dei problemi per l'utilizzo di SQL Server 2017 in Linux.
author: annashres
ms.author: anshrest
manager: craigg
ms.date: 04/30/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 99636ee8-2ba6-4316-88e0-121988eebcf9S
ms.openlocfilehash: e699d921a6100c3f8381b4a5ad1ba3054c258961
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="troubleshoot-sql-server-on-linux"></a>Risolvere i problemi relativi a SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo documento viene descritto come risolvere i problemi relativi a Microsoft SQL Server in esecuzione in Linux o in un contenitore Docker. Quando la risoluzione dei problemi di SQL Server in Linux, è necessario esaminare le funzionalità supportate e le limitazioni note nel [SQL su note sulla versione di Linux](sql-server-linux-release-notes.md).

> [!TIP]
> Per le risposte alle domande più frequenti, vedere il [SQL Server in domande frequenti su Linux](sql-server-linux-faq.md).

## <a id="connection"></a> Risoluzione dei problemi di connessione
Se si verificano problemi di connessione a SQL Server Linux, esistono alcuni elementi da controllare. 

- Verificare che il nome del server o l'indirizzo IP sia raggiungibile dal computer client.

   > [!TIP]
   > Per trovare l'indirizzo IP del computer Ubuntu, è possibile eseguire il comando ifconfig come nell'esempio seguente:
   >
   >   ```bash
   >   sudo ifconfig eth0 | grep 'inet addr'
   >   ```
   > Per Red Hat, è possibile utilizzare l'indirizzo ip come nell'esempio seguente:
   >
   >   ```bash
   >   sudo ip addr show eth0 | grep "inet"
   >   ```
   > Un'eccezione a questa tecnica si riferisce alle macchine virtuali di Azure. Per le macchine virtuali di Azure, [trovare l'indirizzo IP pubblico per la macchina virtuale nel portale di Azure](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#connect).

- Se applicabile, controllare che sia aperta la porta di SQL Server (valore predefinito 1433) nel firewall.

- Per le macchine virtuali di Azure, verificare di avere un [regola gruppo di sicurezza di rete per la porta di SQL Server predefinita](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#remote).

- Verificare che il nome utente e la password non contenga errori di digitazione o spazi aggiuntivi o maiuscole e minuscole non corretta.

- Tenta di impostare in modo esplicito il numero di porta e protocollo con il nome del server come nell'esempio seguente: **tcp:servername, 1433**.

- Problemi di connettività di rete possono causare errori di connessione e timeout. Dopo aver verificato le informazioni di connessione e la connettività di rete, provare a riconnettersi.

## <a name="manage-the-sql-server-service"></a>Gestire il servizio SQL Server

Nelle sezioni seguenti viene illustrato come avviare, arrestare, riavviare e controllare lo stato del servizio SQL Server. 

### <a name="manage-the-mssql-server-service-in-red-hat-enterprise-linux-rhel-and-ubuntu"></a>Gestire il servizio mssql server Red Hat Enterprise Linux (RHEL) e Ubuntu 

Verificare lo stato del servizio SQL Server con il seguente comando:

   ```bash
   sudo systemctl status mssql-server
   ```

È possibile arrestare, avviare o riavviare il servizio SQL Server in base alle esigenze utilizzando i comandi seguenti:

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl start mssql-server
   sudo systemctl restart mssql-server
   ```

### <a name="manage-the-execution-of-the-mssql-docker-container"></a>Gestire l'esecuzione del contenitore Docker mssql

È possibile ottenere l'ID di contenitore e lo stato della versione più recente contenitore Docker di SQL Server creato eseguendo il comando seguente (incluso l'ID di **ID contenitore** colonna):

   ```bash
   sudo docker ps -l
   ```
   
È possibile arrestare o riavviare il servizio SQL Server in base alle esigenze utilizzando i comandi seguenti:
   
   ```bash
   sudo docker stop <container ID>
   sudo docker restart <container ID>
   ```

> [!TIP]
> Per altri suggerimenti sulla risoluzione dei problemi per Docker, vedere [contenitori di risoluzione dei problemi di SQL Server Docker](sql-server-linux-configure-docker.md#troubleshooting).

## <a name="access-the-log-files"></a>Accedere ai file di log
   
I log del motore di SQL Server per il file /var/opt/mssql/log/errorlog nelle installazioni di Linux e Docker. È necessario essere in modalità 'utente avanzato' per passare a questa directory.

Il programma di installazione Registra qui: / var opt/mssql/installazione-< timestamp che rappresenta l'ora di installazione > è possibile esplorare i file di log degli errori con qualsiasi strumento compatibile UTF-16 come 'vim' o 'cat' come segue: 

   ```bash
   sudo cat errorlog
   ```

Se si preferisce, è anche possibile convertire i file UTF-8 per leggerli con 'altro' o 'meno' con il comando seguente:
   
   ```bash
   sudo iconv –f UTF-16LE –t UTF-8 <errorlog> -o <output errorlog file>
   ```
## <a name="extended-events"></a>Eventi estesi

È possibile eseguire query di eventi estesi tramite un comando SQL.  Sono disponibili ulteriori informazioni sugli eventi estesi [qui](https://technet.microsoft.com/en-us/library/bb630282.aspx):

## <a name="crash-dumps"></a>Dump di arresto anomalo 

Cercare dump nella directory dei log in Linux. Verificare nella directory /var/opt/mssql/log Linux Core dump (. tar.gz2 estensione) o SQL minidump (con estensione con estensione mdmp)

Per i dump di Core 
   ```bash
   sudo ls /var/opt/mssql/log | grep .tar.gz2 
   ```

Per i dump SQL 
   ```bash
   sudo ls /var/opt/mssql/log | grep .mdmp 
   ```
   
## <a name="start-sql-server-in-minimal-configuration-or-in-single-user-mode"></a>Avvio di SQL Server nella configurazione minima o in modalità utente singolo

### <a name="start-sql-server-in-minimal-configuration-mode"></a>Avvio di SQL Server in modalità configurazione minima
È utile nel caso in cui l'impostazione di un valore di configurazione, ad esempio un'allocazione eccessiva di memoria, abbia impedito l'avvio del server.
  
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -f
   ```

### <a name="start-sql-server-in-single-user-mode"></a>Avvio di SQL Server in modalità utente singolo
In determinate circostanze, è possibile avviare un'istanza di SQL Server in modalità utente singolo utilizzando l'opzione di avvio -m. Ad esempio, può risultare utile modificare le opzioni di configurazione del server oppure recuperare un database master o un altro database di sistema danneggiato. Ad esempio, è consigliabile modificare le opzioni di configurazione di server oppure recuperare un database master danneggiato o altri database di sistema   

Avvio di SQL Server in modalità utente singolo
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m
   ```

Avvio di SQL Server in modalità utente singolo con SQLCMD
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m SQLCMD
   ```
  
> [!WARNING]  
>  Avviare SQL Server in Linux con l'utente "mssql" per evitare problemi di avvio futuri. Esempio "sudo -u mssql /opt/mssql/bin/sqlservr [STARTUP OPTIONS]" 

Se si è iniziato a accidentalmente SQL Server con un altro utente, è necessario modificare la proprietà del file di database di SQL Server all'utente prima dell'avvio di SQL Server con systemd 'mssql'. Ad esempio, eseguire il comando seguente per modificare la proprietà di tutti i file di database in /var/opt/mssql all'utente 'mssql',

   ```bash
   chown -R mssql:mssql /var/opt/mssql/
   ```

## <a name="rebuild-system-databases"></a>Ricompilare database di sistema
Come ultima risorsa, è possibile scegliere di rigenerare il master ed eseguire il modello di database per le versioni predefinite.

> [!WARNING]
> Questi passaggi verranno **eliminare tutti i dati di sistema di SQL Server** che è stata configurata. Sono incluse informazioni sui database utente (ma non i database utente). Verranno eliminate anche altre informazioni archiviate nei database di sistema, inclusi i seguenti: le informazioni chiave master, tutti i certificati caricati nel database master, la password di account di accesso SA e informazioni relative ai processi da msdb, le informazioni di posta elettronica database msdb e opzioni di sp_configure. Utilizzare solo se si comprendono le implicazioni!

1. Arrestare SQL Server.

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Eseguire **sqlservr** con il **force-setup** parametro. 

   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr --force-setup
   ```
   
   > [!WARNING]
   > Vedere l'avviso precedente! Inoltre, è necessario eseguire questo elemento come il **mssql** utente, come illustrato di seguito.

1. Dopo aver visualizzato il messaggio "Ripristino è stato completato", preme CTRL + C. Verrà arrestato SQL Server

1. Riconfigurare le password dell'account SA.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-sa-password
   ```
   
1. Avvio di SQL Server e riconfigurare il server. Ciò include il ripristino o ricollegare tutti i database utente.

   ```bash
   sudo systemctl start mssql-server
   ```

## <a name="common-issues"></a>Problemi comuni

1. È possibile connettersi all'istanza di SQL Server remoto.

   Vedere la sezione sulla risoluzione dei problemi dell'articolo, [Connetti a SQL Server in Linux](#connection).

2. Errore: Nome host deve essere 15 caratteri o meno.

   Si tratta di un problema noto che si verifica ogni volta che il nome del computer che sta tentando di installare il pacchetto Debian di SQL Server è più lungo di 15 caratteri. Non esistono attualmente alcuna soluzione alternativa diverso da modificare il nome del computer. Un modo per ottenere questo risultato è modificando il file di nome host e il computer verrà riavviato. Nell'esempio [Guida sito Web](http://www.cyberciti.biz/faq/ubuntu-change-hostname-command/) si illustra in dettaglio.

3. Reimpostazione della password di amministrazione (SA) di sistema.

   Se si hanno dimenticato la password di amministratore (SA) di sistema o è necessario reimpostare il valore per altri motivi, seguire questi passaggi.

   > [!NOTE]
   > La procedura seguente arresta temporaneamente il servizio SQL Server.

   Accedere al terminale di host, eseguire i comandi seguenti e seguire le istruzioni per reimpostare la password dell'amministratore di sistema:

   ```bash
   sudo systemctl stop mssql-server
   sudo /opt/mssql/bin/mssql-conf setup
   ```

4. Utilizzo di caratteri speciali nella password.

   Se si usano alcuni caratteri della password di account di accesso di SQL Server, potrebbe essere necessario utilizzare caratteri di escape con una barra rovesciata quando vengono utilizzati in un comando di Linux nei Servizi terminal. Ad esempio, è necessario eseguire l'escape del dollaro ($) ogni volta che si usa in uno script shell dei comandi/terminal:

   Non funziona:

   ```bash
   sudo sqlcmd -S myserver -U sa -P Test$$
   ```

   Funzionamento:

   ```bash
   sqlcmd -S myserver -U sa -P Test\$\$
   ```

   Risorse: [caratteri speciali](http://tldp.org/LDP/abs/html/special-chars.html)
   [Escaping](http://tldp.org/LDP/abs/html/escapingsection.html)

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]
