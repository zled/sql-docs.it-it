---
title: Configurare le impostazioni di SQL Server in Linux | Documenti Microsoft
description: In questo argomento viene descritto come utilizzare lo strumento mssql conf per configurare le impostazioni di SQL Server 2017 in Linux.
author: luisbosquez
ms.author: lbosq
manager: jhubbard
ms.date: 08/24/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 06798dff-65c7-43e0-9ab3-ffb23374b322
ms.translationtype: MT
ms.sourcegitcommit: 46b16dcf147dbd863eec0330e87511b4ced6c4ce
ms.openlocfilehash: 5147b648f2b34496bc46f756639ded028b01fe0e
ms.contentlocale: it-it
ms.lasthandoff: 09/05/2017

---
# <a name="configure-sql-server-on-linux-with-the-mssql-conf-tool"></a>Configurare SQL Server in Linux con lo strumento mssql conf

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

**MSSQL-conf** è uno script di configurazione installato con SQL Server 2017 RC2 per Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Ubuntu. È possibile utilizzare questa utilità per impostare i parametri seguenti:

|||
|---|---|
| [Confronto](#collation) | Impostare nuove regole di confronto per SQL Server in Linux. |
| [Suggerimenti dei clienti](#customerfeedback) | Scegliere se SQL Server Invia commenti e suggerimenti a Microsoft. |
| [Profilo di Posta elettronica database](#dbmail) | Impostare il profilo di posta elettronica database predefinito per SQL Server in Linux |
| [Directory predefinita dei dati](#datadir) | Modificare la directory predefinita per i nuovi file di dati SQL Server database (con estensione mdf). |
| [Directory predefinita log](#datadir) | Modifica la directory predefinita per i nuovi file di log (ldf) di database di SQL Server. |
| [Directory dump predefinita](#dumpdir) | Modificare la directory predefinita per nuovi dump della memoria e altri file di risoluzione dei problemi. |
| [Directory di backup predefinita](#backupdir) | Modificare la directory predefinita per i nuovi file di backup. |
| [Tipo di immagine](#coredump) | Scegliere il tipo di file per raccogliere dump della memoria dump. |
| [Disponibilità elevata](#hadr) | Abilitare gruppi di disponibilità. |
| [Directory di controllo locale](#localaudit) | Impostare una directory da aggiungere i file di controllo locale. |
| [Impostazioni locali](#lcid) | Configurare le impostazioni locali per SQL Server da utilizzare. |
| [Limite di memoria](#memorylimit) | Impostare il limite di memoria per SQL Server. |
| [Porta TCP](#tcpport) | Modificare la porta in cui SQL Server è in ascolto per le connessioni. |
| [TLS](#tls) | Configurare la protezione del trasporto. |
| [Flag di traccia](#traceflags) | Impostare i flag di traccia che il servizio che verrà utilizzata. |

> [!TIP]
> Alcune di queste impostazioni possono essere configurate anche con le variabili di ambiente. Per ulteriori informazioni, vedere [le impostazioni di configurazione SQL Server con le variabili di ambiente](sql-server-linux-configure-environment-variables.md).

## <a name="usage-tips"></a>Suggerimenti per l'utilizzo

* Per i gruppi di disponibilità AlwaysOn e i cluster di dischi condivisi, verificare sempre le stesse modifiche alla configurazione su ciascun nodo.

* Per lo scenario di cluster disco condiviso, non tentare di riavviare il **mssql server** il servizio per applicare le modifiche. SQL Server è in esecuzione come un'applicazione. In alternativa, portare la risorsa non in linea e quindi di nuovo online.

* Questi esempi Esegui mssql-conf per specificare il percorso completo: **/opt/mssql/bin/mssql-conf**. Se si sceglie di passare a tale percorso, invece, è possibile eseguire mssql conf nel contesto della directory corrente: **. / mssql conf**.

## <a id="collation"></a>Modificare le regole di confronto di SQL Server

Il **set di regole di confronto** opzione consente di modificare il valore delle regole di confronto per le regole di confronto supportate:

1. Eseguire il **set di regole di confronto** opzione e seguire le istruzioni:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-collation
   ```

1. L'utilità mssql conf tenta di ripristinare i database utilizzando le regole di confronto specificato e riavviare il servizio. Se sono presenti errori, viene eseguito il rollback nuovamente le regole di confronto per il valore precedente.

Per un elenco di regole di confronto supportate, eseguire il [fn_helpcollations](../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md) funzione: `SELECT Name from sys.fn_helpcollations()`.

## <a id="customerfeedback"></a>Configurare i suggerimenti dei clienti

Il **telemetry.customerfeedback** modifiche alle impostazioni, se SQL Server Invia commenti e suggerimenti a Microsoft o non. Per impostazione predefinita, questo valore è impostato su **true**. Per modificare il valore, eseguire i comandi seguenti:

1. Eseguire lo script mssql conf come radice con il **impostare** comando **telemetry.customerfeedback**. Nell'esempio seguente consente di disattivare i suggerimenti dei clienti specificando **false**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. Riavviare il servizio SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

Per ulteriori informazioni, vedere [i suggerimenti dei clienti per SQL Server in Linux](sql-server-linux-customer-feedback.md).

## <a id="datadir"></a>Modificare il percorso della directory predefinita dati o di log

Il **filelocation.defaultdatadir** e **filelocation.defaultlogdir** le impostazioni di modificare il percorso in cui vengono creati i nuovi file di database e di log. Per impostazione predefinita, questo percorso è /var/opt/mssql/data. Per modificare queste impostazioni, utilizzare la procedura seguente:

1. Creare la directory di destinazione per il nuovo database i file di dati e di log. L'esempio seguente crea un nuovo **/tmp/dati** directory:

   ```bash
   sudo mkdir /tmp/data
   ```

1. Modificare il proprietario e il gruppo della directory in cui il **mssql** utente:

   ```bash
   sudo chown mssql /tmp/data
   sudo chgrp mssql /tmp/data
   ```

1. Utilizzare mssql conf per modificare la directory predefinita dati con il **impostare** comando:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdatadir /tmp/data
   ```

1. Riavviare il servizio SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

1. Tutti i file di database per i nuovi database creati verranno ora essere archiviati nella nuova posizione. Se si desidera modificare il percorso dei file di log (ldf) dei nuovi database, è possibile utilizzare il comando "set" seguente:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultlogdir /tmp/log
   ```

1. Questo comando si presuppone inoltre che esista una directory di log/tmp e che sia in cui l'utente e gruppo **mssql**.

## <a id="dumpdir"></a>Modificare il percorso di directory dump predefinito

Il **filelocation.defaultdumpdir** il percorso predefinito in cui la memoria e dump SQL vengono generati ogni volta che si verifica un arresto anomalo di modifiche alle impostazioni. Per impostazione predefinita, questi file vengono generati in /var/opt/mssql/log.

Per impostare la nuova posizione, utilizzare i comandi seguenti:

1. Creare la directory di destinazione per i nuovi file di dump. L'esempio seguente crea un nuovo **/tmp/dump** directory:

   ```bash
   sudo mkdir /tmp/dump
   ```

1. Modificare il proprietario e il gruppo della directory in cui il **mssql** utente:

   ```bash
   sudo chown mssql /tmp/dump
   sudo chgrp mssql /tmp/dump
   ```

1. Utilizzare mssql conf per modificare la directory predefinita dati con il **impostare** comando:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdumpdir /tmp/dump
   ```

1. Riavviare il servizio SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="backupdir"></a>Modificare il percorso di directory di backup predefinito

Il **filelocation.defaultbackupdir** modifiche alle impostazioni il percorso predefinito in cui vengono generati i file di backup. Per impostazione predefinita, questi file vengono generati in /var/opt/mssql/data.

Per impostare la nuova posizione, utilizzare i comandi seguenti:

1. Creare la directory di destinazione per i nuovi file di backup. L'esempio seguente crea un nuovo **/tmp/backup** directory:

   ```bash
   sudo mkdir /tmp/backup
   ```

1. Modificare il proprietario e il gruppo della directory in cui il **mssql** utente:

   ```bash
   sudo chown mssql /tmp/backup
   sudo chgrp mssql /tmp/backup
   ```

1. Per modificare la directory di backup predefinita con il comando "set", utilizzare mssql conf:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultbackupdir /tmp/backup
   ```

1. Riavviare il servizio SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="coredump"></a>Specificare le impostazioni dell'immagine di base

Se si verifica un'eccezione in uno dei processi di SQL Server, SQL Server crea un dump di memoria.

Sono disponibili due opzioni per il controllo del tipo di memoria dump raccolti da SQL Server: **coredump.coredumptype** e **coredump.captureminiandfull**. Tali elementi sono correlati a due fasi di acquisizione di componenti di base del dump. 

La prima acquisizione fase viene controllata dal **coredump.coredumptype** impostazioni che determinano il tipo di file di dump generati durante un'eccezione. La seconda fase viene abilitata durante il **coredump.captureminiandfull** impostazione. Se **coredump.captureminiandfull** è impostata su true, il dump del file specificato da **coredump.coredumptype** viene generato e viene generato anche un breve dump secondo. Impostazione **coredump.captureminiandfull** su false disabilita l'acquisizione secondo tentativo.

1. Decidere se acquisire un dump completo sia mini con il **coredump.captureminiandfull** impostazione.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.captureminiandfull <true or false>
    ```

    Impostazione predefinita: **false**

1. Specificare il tipo di file dump con il **coredump.coredumptype** impostazione.

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.coredumptype <dump_type>
    ```

    Impostazione predefinita: **miniplus**

    Nella tabella seguente sono elencati i possibili **coredump.coredumptype** valori.

    | Tipo | Description |
    |-----|-----|
    | **mini** | Mini è il più piccolo tipo di file di dump. Usa le informazioni di sistema di Linux per determinare il thread e i moduli del processo. Il dump contiene solo i moduli e gli stack di thread di ambiente host. Non contiene riferimenti di memoria indiretto o globali. |
    | **miniplus** | MiniPlus è simile a mini, ma include memoria aggiuntiva. Riconosce le caratteristiche interne di SQLPAL e l'ambiente host, aggiungere le seguenti aree di memoria per il dump:</br></br> -Varie funzioni globali</br> -Tutta la memoria oltre 64TB</br> -All denominata area trovata nella **/proc/$ pid e mappe**</br> -Memoria indiretto dal thread e stack</br> -Informazioni sul thread</br> -Del Teb e associati di Peb</br> -Informazioni sul modulo</br> -Struttura ad albero VMM e VAD |
    | **filtrati** | Progettazione filtrato viene utilizzata una sottrazione basate su tutta la memoria del processo in cui è inclusa specificamente esclusi. La struttura in grado di comprendere le caratteristiche interne di SQLPAL e l'ambiente host, escludendo il dump di determinate aree geografiche.
    | **completo** | Completa un dump del processo completo che include tutte le aree si trova **/proc/$ pid e mappe**. Non è controllato dalla **coredump.captureminiandfull** impostazione. |

## <a id="dbmail"></a>Impostare il profilo di posta elettronica database predefinito per SQL Server in Linux

Il **sqlpagent.databasemailprofile** consente di impostare il profilo di posta elettronica database predefinito per gli avvisi di posta elettronica.

```bash
sudo /opt/mssq/bin/mssql-conf set sqlagent.databasemailprofile <profile_name>
```
## <a id="hadr"></a>Disponibilità elevata

Il **hadr.hadrenabled** opzione Abilita gruppi di disponibilità nell'istanza di SQL Server. Il seguente comando abilita gruppi di disponibilità impostando **hadr.hadrenabled** su 1. È necessario riavviare SQL Server per l'impostazione per rendere effettive.

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

Per informazioni di utilizzo con gruppi di disponibilità, vedere i seguenti due argomenti.

- [Configurare il gruppo di disponibilità AlwaysOn per SQL Server in Linux](sql-server-linux-availability-group-configure-ha.md)
- [Configurare il gruppo di disponibilità a livello di lettura per SQL Server in Linux](sql-server-linux-availability-group-configure-rs.md)

## <a id="localaudit"></a>Directory del set di controllo locale

Il **telemetry.userrequestedlocalauditdirectory** impostazione Abilita controllo locale e consente di impostare la directory in cui i locale registri di controllo vengono creati.

1. Creare una directory di destinazione per i nuovi log di controllo locale. L'esempio seguente crea un nuovo **/tmp/controllo** directory:

   ```bash
   sudo mkdir /tmp/audit
   ```

1. Modificare il proprietario e il gruppo della directory in cui il **mssql** utente:

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

1. Eseguire lo script mssql conf come radice con il **impostare** comando **telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

1. Riavviare il servizio SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

Per ulteriori informazioni, vedere [i suggerimenti dei clienti per SQL Server in Linux](sql-server-linux-customer-feedback.md).

## <a id="lcid"></a>Modificare le impostazioni locali di SQL Server

Il **language.lcid** modifiche alle impostazioni locali di SQL Server a qualsiasi identificatore di lingua supportata (LCID). 

1. Nell'esempio seguente modifica le impostazioni locali sulla lingua francese (1036):

   ```bash
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
   ```

1. Riavviare il servizio SQL Server per applicare le modifiche:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="memorylimit"></a>Impostare il limite di memoria

Il **memory.memorylimitmb** impostazione quantità memoria fisica (in MB) disponibile per SQL Server. Il valore predefinito è 80% della memoria fisica.

1. Eseguire lo script mssql conf come radice con il **impostare** comando **memory.memorylimitmb**. L'esempio seguente modifica la memoria disponibile per SQL Server a 3,25 GB (3328 MB).

   ```bash
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
   ```

1. Riavviare il servizio SQL Server per applicare le modifiche:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="tcpport"></a>Modificare la porta TCP

Il **network.tcpport** quando si imposta la porta TCP in cui SQL Server è in ascolto per le connessioni. Per impostazione predefinita, questa porta è 1433. Per modificare la porta, eseguire i comandi seguenti:

1. Eseguire lo script mssql conf come radice con il comando "set" per "network.tcpport":

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.tcpport <new_tcp_port>
   ```

1. Riavviare il servizio SQL Server:

   ```bash
   sudo systemctl restart mssql-server
   ```

1. Quando ci si connette a SQL Server, è necessario specificare la porta personalizzata con una virgola (,) dopo il nome host o indirizzo IP. Per connettersi con SQLCMD, ad esempio, utilizzare il comando seguente:

   ```bash
   sqlcmd -S localhost,<new_tcp_port> -U test -P test
   ```

## <a id="tls"></a>Specificare le impostazioni di TLS

Le opzioni seguenti configurare TLS per un'istanza di SQL Server in esecuzione in Linux.

|Opzione |Description |
|--- |--- |
|**Network.forceencryption** |Se è 1, quindi [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] forza tutte le connessioni da crittografare. Per impostazione predefinita, questa opzione è 0. |
|**Network.tlscert** |Il percorso assoluto per il certificato di file che [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizza per TLS. Esempio: `/etc/ssl/certs/mssql.pem` il file del certificato deve essere accessibile dall'account mssql. Si consiglia di limitare l'accesso al file usando `chown mssql:mssql <file>; chmod 400 <file>`. |
|**Network.tlskey** |Il percorso assoluto per la chiave privata del file che [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizza per TLS. Esempio: `/etc/ssl/private/mssql.key` il file del certificato deve essere accessibile dall'account mssql. Si consiglia di limitare l'accesso al file usando `chown mssql:mssql <file>; chmod 400 <file>`. |
|**Network.tlsprotocols** |Elenco delimitato da virgole di quali TLS sono consentiti i protocolli da SQL Server. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]tenta sempre di negoziazione del protocollo consentito più attendibili. Se un client non supporta alcun protocollo consentito, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] rifiuta il tentativo di connessione.  Per garantire la compatibilità, sono consentiti tutti i protocolli supportati per impostazione predefinita (1.2, 1.1, 1.0).  Se i client supportano TLS 1.2, si consiglia di consentire solo TLS 1.2. |
|**Network.tlsciphers** |Specifica le crittografie consentite dal [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per TLS. Questa stringa deve essere formattata [formato di elenco di pacchetti di crittografia di OpenSSL](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html). In generale, non è necessario modificare questa opzione. <br /> Per impostazione predefinita, sono consentite le crittografie seguenti: <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |
| **Network.kerberoskeytabfile** |Percorso del file keytab Kerberos |

Per un esempio di usando le impostazioni di TLS, vedere [crittografia delle connessioni a SQL Server in Linux](sql-server-linux-encrypted-connections.md).

## <a id="traceflags"></a>Abilitare o disabilitare i flag di traccia

Questo **traceflag** opzione Abilita o disabilita i flag di traccia per l'avvio del servizio SQL Server. Per abilitare o disabilitare un flag di traccia, utilizzare i comandi seguenti:

1. Abilitare un flag di traccia utilizzando il comando seguente. Ad esempio, per i flag di traccia 1234:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 on
   ```

1. È possibile abilitare i flag di traccia più specificandoli separatamente:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 2345 3456 on
   ```

1. In modo analogo, è possibile disabilitare uno o più flag di traccia abilitato specificarli e aggiungendo il **off** parametro:

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 2345 3456 off
   ```

1. Riavviare il servizio SQL Server per applicare le modifiche:

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="remove-a-setting"></a>Rimuovere un'impostazione

Per annullare qualsiasi impostazione effettuata con `mssql-conf set`, chiamare **mssql conf** con il `unset` opzione e il nome dell'impostazione. Questo Cancella l'impostazione, in modo efficace restituirlo al valore predefinito.

1. Nell'esempio seguente viene cancellato il **network.tcpport** opzione.

   ```bash
   sudo /opt/mssql/bin/mssql-conf unset network.tcpport
   ```

1. Riavviare il servizio SQL Server.

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="view-current-settings"></a>Visualizzare le impostazioni correnti

Per visualizzare le impostazioni configurate e eseguire il comando seguente per generare il contenuto del **mssql.conf** file:

```bash
sudo cat /var/opt/mssql/mssql.conf
```

Si noti che le impostazioni non è state illustrate in questo file utilizza valori predefiniti. La sezione successiva viene fornito un esempio **mssql.conf** file.

## <a name="mssqlconf-format"></a>formato MSSQL.conf

Nell'esempio **/var/opt/mssql/mssql.conf** file viene fornito un esempio per ogni impostazione. È possibile utilizzare questo formato apportare manualmente modifiche per il **mssql.conf** file in base alle esigenze. Se si modifica manualmente il file, è necessario riavviare SQL Server prima che vengano applicate le modifiche. Utilizzare il **mssql.conf** file con Docker, è necessario disporre di Docker [i dati persistenti](sql-server-linux-configure-docker.md). Aggiungere prima un completo **mssql.conf** file nella directory di host e quindi eseguire il contenitore. Un esempio di questo tipo in [i suggerimenti dei clienti](sql-server-linux-customer-feedback.md).

```ini
[EULA]
accepteula = Y

[coredump]
captureminiandfull = true
coredumptype = full

[filelocation]
defaultbackupdir = /var/opt/mssql/data/
defaultdatadir = /var/opt/mssql/data/
defaultdumpdir = /var/opt/mssql/data/
defaultlogdir = /var/opt/mssql/data/

[hadr]
hadrenabled = 0

[language]
lcid = 1033

[memory]
memorylimitmb = 4096

[network]
forceencryption = 0
ipaddress = 10.192.0.0
kerberoskeytabfile = /var/opt/mssql/secrets/mssql.keytab
tcpport = 1401
tlscert = /etc/ssl/certs/mssql.pem
tlsciphers = ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA
tlskey = /etc/ssl/private/mssql.key
tlsprotocols = 1.2,1.1,1.0

[sqlagent]
databasemailprofile = default
errorlogfile = /var/opt/mssql/log/sqlagentlog.log
errorlogginglevel = 7

[telemetry]
customerfeedback = true
userrequestedlocalauditdirectory = /tmp/audit

[traceflag]
traceflag0 = 1204
traceflag1 = 2345
traceflag = 3456
```

## <a name="next-steps"></a>Passaggi successivi

Per utilizzare le variabili di ambiente per apportare queste modifiche alla configurazione, vedere [le impostazioni di configurazione SQL Server con le variabili di ambiente](sql-server-linux-configure-environment-variables.md).

Per altri scenari e strumenti di gestione, vedere [gestire SQL Server in Linux](sql-server-linux-management-overview.md).

