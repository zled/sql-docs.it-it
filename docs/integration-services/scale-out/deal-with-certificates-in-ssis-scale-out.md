---
title: Gestire i certificati in Sql Server Integration Services Scale Out | Documenti Microsoft
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2970b2b2cc7cf30c18a203ebbb92b5418bfc9be5
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="deal-with-certificates-in-sql-server-integration-services-scale-out"></a>Gestire i certificati in SQL Server Integration Services scalabile

Per proteggere la comunicazione tra scala Out Master e scala Out Worker, due certificati vengono utilizzati in scala Out, ad esempio scala Out Master e certificato scala il lavoro. 

## <a name="scale-out-master-certificate"></a>Scala Out Master certificato

Nella maggior parte dei casi, il certificato di scala Out Master è configurato durante l'installazione di scala Out Master.

Nel **scala Out configurazione di Integration Services - nodo Master** pagina della procedura guidata di installazione di SQL Server, è possibile scegliere di creare un nuovo certificato SSL autofirmato o usare un certificato SSL esistente.

![Configurazione generale](media/master-config.PNG)

Se non si dispone di requisiti speciali sui certificati, è possibile scegliere di creare un nuovo certificato SSL autofirmato. È possibile specificare ulteriormente il CN nel certificato. Assicurarsi che il nome host dell'endpoint del master utilizzata in un secondo momento da scala il processo di lavoro è incluso nel CN. Per impostazione predefinita, sono inclusi il nome del computer e l'indirizzo ip di nodo principale. 

Se si sceglie di usare un certificato esistente, fare clic su "Sfoglia …" per selezionare un certificato SSL da **radice** archivio certificati del computer locale.

### <a name="change-scale-out-master-certificate"></a>Scala Out Master Cambia certificato

È consigliabile modificare il certificato di scala Out Master a causa di scadenza dei certificati o altri motivi. Attenersi alla procedura seguente:

#### <a name="1-create-a-ssl-certificate"></a>1. Creare un certificato SSL.
Creare e installare un certificato SSL sul Master nodo con il comando seguente:
```dos
MakeCert.exe -n CN={master endpoint host} SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```
Esempio:
```dos
MakeCert.exe -n CN=MasterMachine SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```

#### <a name="2-bind-the-certificate-to-master-port"></a>2. Associare il certificato al server principale porta
Controllare l'associazione originale con il comando:
```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```
Esempio:
```dos
netsh http show sslcert ipport=0.0.0.0:8391
```
Eliminare l'associazione originale e impostare la nuova associazione con i comandi seguenti:
```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={SSL Certificate Thumbprint} certstorename=Root appid={original appid}
```
Esempio:
```dos
netsh http delete sslcert ipport=0.0.0.0:8391
netsh http add sslcert ipport=0.0.0.0:8391 certhash=01d207b300ca662f479beb884efe6ce328f77d53 certstorename=Root appid={a1f96506-93e0-4c91-9171-05a2f6739e13}
```
#### <a name="3-update-scale-out-master-service-configuration-file"></a>3. Aggiornare il file di configurazione servizio scala Out Master
Aggiornamento scala Out Master del servizio file di configurazione \<driver\>: \Programmi\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config, sul Master nodo. Aggiornamento **SSLCertThumbprint** all'identificazione personale del nuovo certificato SSL.

#### <a name="4-restart-scale-out-master-service"></a>4. Riavviare il servizio di scala Out Master

#### <a name="5-reconnect-scale-out-worker-to-scale-out-master"></a>5. Riconnettersi scalabilità lavoro a scalabilità orizzontale Master
Per ogni scala i thread di lavoro, eliminare il processo di lavoro e aggiungerlo di nuovo con [scala Out Manager](integration-services-ssis-scale-out-manager.md) o seguire i passaggi 5.1 a 5.3:

5.1 installare il certificato SSL client nell'archivio radice del computer locale nel nodo di lavoro

5.2 aggiornamento della scala Out lavoro servizio configurazione file scala Out lavoro aggiornamento file di configurazione servizio \<driver\>: \Programmi\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config, nel nodo di lavoro. Aggiornamento **MasterHttpsCertThumbprint** all'identificazione personale del nuovo certificato SSL.

5.3 scala di riavviare il servizio ruolo di lavoro


## <a name="scale-out-worker-certificate"></a>Certificato di scala Out lavoro

Certificato di scala il lavoro viene generato automaticamente durante l'installazione di scala il lavoro. 

### <a name="change-scale-out-worker-certificate"></a>Cambia certificato scala Out lavoro

In casi che si desidera modificare il certificato di scala il lavoro, attenersi alla procedura seguente.

#### <a name="1-create-a-certificate"></a>1. Creare un certificato
Creare e installare un certificato con il comando seguente:
```dos
MakeCert.exe -n CN={worker machine name};CN={worker machine ip} SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
Esempio:
```dos
MakeCert.exe -n CN=WorkerMachine;CN=10.0.2.8 SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
#### <a name="2-install-the-client-certificate-to-the-root-store-of-local-machine-on-worker-node"></a>2. Installare il certificato client nell'archivio radice del computer locale nel nodo di lavoro

#### <a name="3-give-service-access-to-the-certificate"></a>3. Accedere al certificato di servizio
Eliminare il certificato precedente e consentire l'accesso di servizio scala il lavoro per il nuovo certificato con il comando:
```dos
certmgr.exe /del /c /s /r localmachine My /n {CN of the old certificate}
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the new certificate} -a {the account running Scale Out Worker service}
```
Esempio:
```dos
certmgr.exe /del /c /s /r localmachine My /n WorkerMachine
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s WorkerMachine -a SSISScaleOutWorker140
```
#### <a name="4-update-scale-out-worker-configuration-file"></a>4. Aggiornare il file di configurazione di scala Out lavoro
File di configurazione servizio scala il lavoro di aggiornamento, \<driver\>: \Programmi\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config, nel nodo di lavoro. Aggiornamento **WorkerHttpsCertThumbprint** all'identificazione personale del nuovo certificato.

#### <a name="5-install-the-client-certificate-to-the-root-store-of-local-machine-on-master-node"></a>5. Installare il certificato client nell'archivio radice del computer locale sul Master nodo

#### <a name="6-restart-scale-out-worker-service"></a>6. Riavviare il servizio di scala Out lavoro

