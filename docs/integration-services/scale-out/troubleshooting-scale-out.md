---
title: Risoluzione dei problemi di SQL Server Integration Services (SSIS) Scale Out | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 56d61bc6ba76514ba2291243002a7423ec8e265c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="troubleshooting-scale-out"></a>Risoluzione dei problemi di Scale Out

SSIS Scale Out richiede la comunicazione tra il database SSISDB, il servizio Scale Out Master e il servizio Scale Out Worker. In alcuni casi la comunicazione viene interrotta a causa di errori di configurazione, mancanza di autorizzazioni di accesso e per altri motivi. Questo documento contiene le informazioni necessarie per risolvere i problemi relativi alla configurazione di Scale Out.

Per analizzare i sintomi riscontrati, seguire uno alla volta i passaggi illustrati di seguito fino alla risoluzione del problema.

### <a name="symptoms"></a>**Sintomi** 
Scale Out Master non si connette al database SSISDB. 

Non è possibile visualizzare le proprietà master in Scale Out Manager.

Le proprietà master non vengono inserite in [SSISDB].[catalog].[master_properties]

### <a name="solution"></a>**Soluzione**
Passaggio 1: Verificare che Scale Out sia abilitato.

Fare clic con il pulsante destro del mouse sul nodo **SSISDB** in Esplora oggetti di SSMS e selezionare **La funzionalità Scale Out è abilitata**.

![Verificare che Scale Out sia abilitato](media\isenabled.PNG)

Se il valore della proprietà è False, abilitare Scale Out chiamando la stored procedure [SSISDB].[catalog].[enable_scaleout].

Passaggio 2: Verificare che il nome SQL Server specificato nel file di configurazione di Scale Out Master sia corretto e riavviare il servizio Scale Out Master.

### <a name="symptoms"></a>**Sintomi** 
Scale Out Worker non si connette a Scale Out Master

Dopo l'aggiunta in Scale Out Manager, Scale Out Worker non viene visualizzato

Scale Out Worker non viene visualizzato in [SSISDB].[catalog].[worker_agents]

Il servizio Scale Out Worker è in esecuzione, mentre Scale Out Worker è offline

### <a name="solutions"></a>**Soluzioni** 
Controllare i messaggi di errore nel log del servizio Scale Out Worker in \<unità\>:\Utenti\\*[account che esegue il servizio worker]*\AppData\Local\SSIS\Cluster\Agent.

**Caso** 

System.ServiceModel.EndpointNotFoundException: Non è disponibile alcun endpoint in ascolto su https://*[NomeComputer]:[Porta]*/ClusterManagement/ in grado di accettare il messaggio.

Passaggio 1: Verificare che il numero di porta specificato nel file di configurazione del servizio Scale Out Master sia corretto e riavviare il servizio Scale Out Master. 

Passaggio 2: Verificare che l'endpoint master specificato nella configurazione del servizio Scale Out Worker sia corretto e riavviare il servizio Scale Out Worker.

Passaggio 3: Verificare che la porta del firewall sia aperta nel nodo Scale Out Master.

Passaggio 4: Risolvere altri eventuali problemi di connessione tra il nodo Scale Out Master e il nodo Scale Out Worker.

**Caso**

System.ServiceModel.Security.SecurityNegotiationException: Impossibile stabilire relazioni di trust per il canale sicuro SSL/TLS con l'autorità "*[NomeComputer]:[Porta]*". ---> System.Net.WebException: Connessione sottostante chiusa: Impossibile stabilire una relazione di trust per il canale sicuro SSL/TLS. ---> System.Security.Authentication.AuthenticationException: Il certificato remoto non è stato ritenuto valido dalla procedura di convalida.

Passaggio 1: Installare il certificato di Scale Out Master nell'archivio radice dei certificati del computer locale nel nodo Scale Out Worker se non è ancora stato installato e riavviare il servizio Scale Out Worker.

Passaggio 2: Verificare che il nome host nell'endpoint master sia incluso nei nomi comuni (CN) del certificato di Scale Out Master. In caso contrario, reimpostare l'endpoint master nel file di configurazione di Scale Out Worker e riavviare il servizio Scale Out Worker. 

> [!Note]
> Se non è possibile modificare il nome host dell'endpoint master a causa delle impostazioni DNS, sarà necessario modificare il certificato di Scale Out Master. Vedere [Gestire i certificati in SSIS Scale Out](deal-with-certificates-in-ssis-scale-out.md).

Passaggio 3: Verificare che l'identificazione personale master specificata nella configurazione di Scale Out Worker corrisponda all'identificazione personale del certificato di Scale Out Master. 

**Caso**

System.ServiceModel.Security.SecurityNegotiationException: Impossibile stabilire un canale sicuro per SSL/TLS con l'autorità "*[NomeComputer]:[Porta]*". ---> System.Net.WebException: Richiesta annullata: Impossibile creare un canale sicuro SSL/TLS.

Passaggio 1: Verificare che l'account che esegue il servizio Scale Out Worker abbia accesso al certificato di Scale Out Worker usando il comando riportato di seguito.

```dos
winhttpcertcfg.exe -l -c LOCAL_MACHINE\MY -s {CN of the worker certificate}
```

Se l'account non ha accesso, concederlo usando il comando seguente e riavviare il servizio Scale Out Worker.

```dos
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the worker certificate} -a {the account running Scale Out Worker service}
```

**Caso**

System.ServiceModel.Security.MessageSecurityException: Richiesta HTTP vietata con lo schema di autenticazione client "Anonimo". ---> System.Net.WebException: Errore del server remoto: (403) Non consentito.

Passaggio 1: Installare il certificato di Scale Out Worker nell'archivio radice dei certificati del computer locale nel nodo Scale Out Master se non è ancora stato installato e riavviare il servizio Scale Out Worker.

Passaggio 2: Eseguire la pulizia dei certificati inutili nell'archivio radice dei certificati del computer locale nel nodo Scale Out Master.

Passaggio 3: Configurare Schannel in modo da non inviare più l'elenco delle autorità di certificazione radice attendibili durante il processo di handshake TLS/SSL aggiungendo la voce del Registro di sistema seguente nel nodo Scale Out Master.

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL

Nome valore: SendTrustedIssuerList 

Tipo valore: REG_DWORD 

Dati valore: 0 (False)

**Caso**

System.ServiceModel.CommunicationException: Errore durante la richiesta HTTP a https://*[NomeComputer]:[Porta]*/ClusterManagement/. È possibile che il certificato server non sia configurato correttamente con HTTP.SYS nel caso HTTPS o che il binding di sicurezza tra il client e il server non corrisponda. 

Passaggio 1: Verificare che il certificato di Scale Out Master sia associato correttamente alla porta nell'endpoint master nel nodo master usando il comando seguente. Verificare se l'hash del certificato visualizzato corrisponde all'identificazione personale del certificato di Scale Out Master.

```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```

Se l'associazione non è corretta, reimpostarla con i comandi seguenti e riavviare il servizio Scale Out Worker.

```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={Master certificate thumbprint} certstorename=Root appid={random guid}
```

### <a name="symptoms"></a>**Sintomi**
Alla connessione di Scale Out Worker a Scale Out Master, la convalida in Scale Out Manager non è riuscita generando il messaggio di errore "Non è possibile aprire l'archivio certificati nel computer".

### <a name="solution"></a>**Soluzione**

Passaggio 1: Eseguire Scale Out Manager come amministratore. Se viene aperto con SSMS sarà necessario eseguire SSMS come amministratore.

Passaggio 2: Avviare il servizio Registro di sistema remoto nel computer, se non è in esecuzione.

### <a name="symptoms"></a>**Sintomi**
Non è possibile avviare l'esecuzione in Scale Out.

### <a name="solution"></a>**Soluzione**

Verificare lo stato dei computer selezionati per l'esecuzione del pacchetto in [SSISDB].[catalog].[worker_agents]. È necessario che almeno un ruolo di lavoro sia online e abilitato.

### <a name="symptoms"></a>**Sintomi** 
I pacchetti vengono eseguiti correttamente, ma non viene registrato alcun messaggio.

### <a name="solution"></a>**Soluzione**

Verificare che l'autenticazione di SQL Server sia consentita dall'istanza di SQL Server che ospita il database SSISDB.

> [!Note]  
> Se è stato modificato l'account per la registrazione di Scale Out, vedere [Modificare l'account per la registrazione di Scale Out](change-logdb-account.md) e verificare la stringa di connessione usata per la registrazione.

### <a name="symptoms"></a>**Sintomi**
I messaggi di errore nel report di esecuzione del pacchetto non sono sufficienti per la risoluzione del problema.

### <a name="solution"></a>**Soluzione**
Altri log di esecuzione sono disponibili nel percorso TasksRootFolder configurato in WorkerSettings.config. Per impostazione predefinita, il percorso è \<unità\>: \Utenti\\*[account]*\AppData\Local\SSIS\ScaleOut\Tasks. *[account]* indica l'account che esegue il servizio Scale Out Worker con il valore predefinito SSISScaleOutWorker140.

Per individuare il log per l'esecuzione del pacchetto con *[execution id]*, eseguire il comando T-SQL seguente per ottenere *[task id]*. Individuare quindi la sottocartella denominata con *[task id]* in TasksRootFolder.<sup>1<sup>

```sql
SELECT [TaskId]
FROM [SSISDB].[internal].[tasks] tasks, [SSISDB].[internal].[executions] executions 
WHERE executions.execution_id = *Your Execution Id* AND tasks.JobId = executions.job_id
```
<sup>1</sup> Questa query è stata creata solo per la risoluzione dei problemi e potrà essere modificata quando lo scenario di registrazione/diagnostica di Scale Out Worker verrà migliorato. 
