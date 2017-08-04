---
title: "Risoluzione dei problemi relativi a SQL Server Integration Services (SSIS) scalabilità | Documenti Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 41bb853dd08591596f6f5baa918e174d0c26a6b5
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="troubleshooting-scale-out"></a>Risoluzione dei problemi di scalabilità orizzontale

SSIS Scale Out implica communtication tra SSISDB, servizi di scala Out Master e scala il lavoro. In alcuni casi, la comunicazione è interrotta a causa di errori di configurazione, mancanza di autorizzazioni di accesso e per altri motivi. Questo documento consente di risolvere i problemi relativi alla configurazione orizzontale.

Per analizzare i problemi riscontrati, seguire questa procedura uno alla volta finché non viene risolto il problema.

### <a name="symptoms"></a>**Sintomi** 
Scala Out Master non è possibile connettersi a SSISDB. 

Proprietà master non è possibile visualizzare in scala Out Manager.

Proprietà master non sono state compilate [SSISDB]. [catalog]. [master_properties]

### <a name="solution"></a>**Soluzione**
Passaggio 1: Verificare se orizzontale è abilitata.

Fare doppio clic su **SSISDB** nodo in Esplora oggetti di SQL Server Management Studio e controllo **è abilitata la funzionalità orizzontale**.

![È scalabile abilitato](media\isenabled.PNG)

Se il valore della proprietà è False, è possibile abilitare orizzontale chiamando stored procedure [SSISDB]. [catalog]. [enable_scaleout].

Passaggio 2: Verificare se il nome di Sql Server specificato nel file di configurazione di scala Out Master sia corretto e riavviare il servizio di scala Out Master.

### <a name="symptoms"></a>**Sintomi** 
Scala il lavoro non è possibile connettersi al scala Out Master

Scala il lavoro non viene visualizzato dopo averlo aggiunto in scala Out Manager

Scala il lavoro non viene visualizzato in [SSISDB]. [catalog]. [worker_agents]

Servizio scala Out Worker è in esecuzione, mentre è in linea scala Out lavoro

### <a name="solutions"></a>**Soluzioni** 
Controllare i messaggi di errore nel registro servizio scala Out lavoro \<driver\>: \Users\\*[account che esegue il servizio di lavoro]*\AppData\Local\SSIS\Cluster\Agent.

**Case** 

EndpointNotFoundException: Si è verificato alcun endpoint in ascolto su https://*[NomeComputer]: [porta]*/ClusterManagement/ in grado di accettare il messaggio.

Passaggio 1: Verificare se il numero di porta specificato nel file di configurazione del servizio di scala Out Master sia corretto e riavviare il servizio di scala Out Master. 

Passaggio 2: Verificare se l'endpoint master specificato nella configurazione del servizio scala Out lavoro sia corretto e riavviare il servizio di scala il lavoro.

Passaggio 3: Verificare se la porta firewall è aperta nel nodo scala Out Master.

Passaggio 4: Risolvere altri problemi di connessione tra nodo di scala Out Master e scala il lavoro.

**Case**

System.ServiceModel.Security.SecurityNegotiationException: Impossibile stabilire una relazione di trust per il canale sicuro SSL/TLS con l'autorità '*[nome macchina]: [porta]*'. ---> System.NET. WebException: connessione sottostante chiusa: Impossibile stabilire una relazione di trust per il canale sicuro SSL/TLS. ---> AuthenticationException: il certificato remoto non è valido in base alla procedura di convalida.

Passaggio 1: Installare scala Out Master certificato all'archivio certificati radice del computer locale nel nodo scala Out lavoro se non è ancora stato installato e riavviare il servizio di scala il lavoro.

Passaggio 2: Controllare se il nome host nell'endpoint master viene incluso nel certificato CN della scala Out Master. In caso contrario, reimpostare l'endpoint master nel file di configurazione di scala il lavoro e riavviare il servizio di scala il lavoro. 

> [!Note]
> Se non è possibile modificare il nome host dell'endpoint master a causa delle impostazioni DNS, è necessario modificare il certificato di scala Out Master. Vedere [gestire certificati in SSIS Scale Out](deal-with-certificates-in-ssis-scale-out.md).

Passaggio 3: Controllare se l'identificazione personale del master specificato nella configurazione di scala Out lavoro corrispondente all'identificazione personale del certificato di scala Out Master. 

**Case**

System.ServiceModel.Security.SecurityNegotiationException: Impossibile stabilire un canale sicuro per SSL/TLS con l'autorità '*[nome macchina]: [porta]*'. ---> System.NET. WebException: la richiesta è stata interrotta: Impossibile creare un canale protetto SSL/TLS.

Passaggio 1: Verificare se l'account che esegue servizio scala Out Worker ha accesso al certificato scala il lavoro tramite il comando riportato di seguito.

```dos
winhttpcertcfg.exe -l -c LOCAL_MACHINE\MY -s {CN of the worker certificate}
```

Se l'account non dispone di accesso, concedere usando il comando seguente e riavviare il servizio di scala il lavoro.

```dos
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the worker certificate} -a {the account running Scale Out Worker service}
```

**Case**

MessageSecurityException: La richiesta HTTP vietata con lo schema di autenticazione client 'Anonymous'. ---> System.NET. WebException: il server remoto ha restituito un errore: (403) accesso negato.

Passaggio 1: Installare scala Out lavoro certificato all'archivio certificati radice del computer locale nel nodo scala Out Master se non è ancora stato installato e riavviare il servizio di scala il lavoro.

Passaggio 2: Eseguire la pulizia delle inutili certificati nell'archivio certificati radice del computer locale nel nodo scala Out Master.

Passaggio 3: Configurare Schannel per non inviare l'elenco di autorità di certificazione radice attendibili durante il processo di handshake TLS/SSL, aggiungendo la voce del Registro di sistema seguente nel nodo scala Out Master.

Hkey_local_machine\system\currentcontrolset\control\securityproviders\schannel.

Nome valore: SendTrustedIssuerList 

Tipo di valore: REG_DWORD 

Dati valore: 0 (False)

**Case**

CommunicationException: Si è verificato un errore durante la richiesta HTTP con https://*[nome macchina]: [porta]*ClusterManagement /. È possibile che il certificato del server non è configurato correttamente con HTTP. SYS nel caso HTTPS. Ciò potrebbe essere causato anche da una mancata corrispondenza di associazione di sicurezza tra il client e server. 

Passaggio 1: Verificare se il certificato di scala Out Master è associato alla porta nell'endpoint master correttamente sul nodo principale con il comando seguente. Controllare se l'hash del certificato visualizzato viene confrontata con identificazione personale del certificato di scala Out Master.

```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```

Se l'associazione non è corretto, ripristinare le impostazioni con i comandi seguenti e riavviare il servizio di scala il lavoro.

```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={Master certificate thumbprint} certstorename=Root appid={random guid}
```

### <a name="symptoms"></a>**Sintomi**
Non si avvia l'esecuzione in orizzontale.

### <a name="solution"></a>**Soluzione**

Verificare lo stato dei computer che si è scelto di eseguire il pacchetto in [SSISDB]. [catalog]. [worker_agents]. Almeno un lavoro deve essere online e abilitato.

### <a name="symptoms"></a>**Sintomi** 
Pacchetti eseguiti correttamente, ma nessun messaggio registrato.

### <a name="solution"></a>**Soluzione**

Controllare se l'autenticazione di SQL Server è consentito da Sql Server che ospita SSISDB.

> [!Note]  
> Se è stato modificato l'account per la registrazione orizzontale, vedere [modificare l'Account per la scala Out registrazione](change-logdb-account.md) e verificare la stringa di connessione utilizzata per la registrazione.

### <a name="symptoms"></a>**Sintomi**
I messaggi di errore nel report di esecuzione del pacchetto non sono sufficienti per la risoluzione dei problemi.

### <a name="solution"></a>**Soluzione**
Più log di esecuzione è reperibile in TasksRootFolder configurato in WorkerSettings.config. Per impostazione predefinita è \<driver\>: \Users\\*[account]*\AppData\Local\SSIS\ScaleOut\Tasks. Il *[account]* è l'account che esegue servizio scala Out Worker con il valore predefinito SSISScaleOutWorker140.

Per individuare il log per l'esecuzione del pacchetto con *[id esecuzione]*, eseguire il comando T-SQL seguente per ottenere il *[id attività]*. Quindi, individuare la sottocartella denominata con *[id attività]* in TasksRootFolder.<sup> 1<sup>

```sql
SELECT [TaskId]
FROM [SSISDB].[internal].[tasks] tasks, [SSISDB].[internal].[executions] executions 
WHERE executions.execution_id = *Your Execution Id* AND tasks.JobId = executions.job_id
```
<sup>1</sup> questa query è per la risoluzione dei problemi relativi a scopo aprire e solo per modificare quando lo scenario di registrazione/diagnostica di scala i thread di lavoro è stato migliorato in futuro. 
