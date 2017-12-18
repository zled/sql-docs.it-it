---
title: Gestire i certificati in SQL Server Integration Services Scale Out | Microsoft Docs
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
ms.openlocfilehash: e09fec1fcf9cf0221dad50d708adef773b297237
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="deal-with-certificates-in-sql-server-integration-services-scale-out"></a>Gestire i certificati in SQL Server Integration Services Scale Out

Per proteggere la comunicazione tra Scale Out Master e Scale Out Worker, in Scale Out vengono usati due certificati, ossia il certificato di Scale Out Master e il certificato di Scale Out Worker. 

## <a name="scale-out-master-certificate"></a>Certificato di Scale Out Master

Nella maggior parte dei casi, il certificato di Scale Out Master viene configurato durante l'installazione di Scale Out Master.

Nella pagina **Configurazione di Integration Services Scale Out - Nodo master** dell'Installazione guidata di SQL Server, è possibile scegliere di creare un nuovo certificato SSL autofirmato oppure usare un certificato SSL esistente.

![Configurazione Master](media/master-config.PNG)

Se non si hanno requisiti speciali per i certificati, è possibile scegliere di creare un nuovo certificato SSL autofirmato. In questo certificato è anche possibile specificare i nomi comuni (CN). Verificare che il nome host dell'endpoint master che sarà poi usato da Scale Out Worker sia incluso nei nomi comuni. Per impostazione predefinita, sono inclusi il nome del computer e l'IP del nodo master. 

Se si sceglie di usare un certificato esistente, fare clic su "Sfoglia …" per selezionare un certificato SSL dall'archivio certificati **Radice** del computer locale.

### <a name="change-scale-out-master-certificate"></a>Modificare il certificato di Scale Out Master

Potrebbe essere necessario modificare il certificato di Scale Out Master perché scaduto o per altri motivi. Attenersi alla procedura seguente:

#### <a name="1-create-a-ssl-certificate"></a>1. Creare un certificato SLL.
Creare e installare un certificato SLL nel nodo master con il comando seguente:
```dos
MakeCert.exe -n CN={master endpoint host} SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```
Esempio:
```dos
MakeCert.exe -n CN=MasterMachine SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```

#### <a name="2-bind-the-certificate-to-master-port"></a>2. Associare il certificato alla porta master
Controllare l'associazione originale con il comando seguente:
```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```
Esempio:
```dos
netsh http show sslcert ipport=0.0.0.0:8391
```
Eliminare l'associazione originale e configurare la nuova associazione con i comandi seguenti:
```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={SSL Certificate Thumbprint} certstorename=Root appid={original appid}
```
Esempio:
```dos
netsh http delete sslcert ipport=0.0.0.0:8391
netsh http add sslcert ipport=0.0.0.0:8391 certhash=01d207b300ca662f479beb884efe6ce328f77d53 certstorename=Root appid={a1f96506-93e0-4c91-9171-05a2f6739e13}
```
#### <a name="3-update-scale-out-master-service-configuration-file"></a>3. Aggiornare il file di configurazione del servizio Scale Out Master
Aggiornare il file di configurazione del servizio Scale Out Master, \<unità\>:\Programmi\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config nel nodo master. Aggiornare **SSLCertThumbprint** all'identificazione personale del nuovo certificato SSL.

#### <a name="4-restart-scale-out-master-service"></a>4. Riavviare il servizio Scale Out Master

#### <a name="5-reconnect-scale-out-worker-to-scale-out-master"></a>5. Ricollegare Scale Out Worker a Scale Out Master
Per ogni istanza di Scale Out Worker, eliminare il ruolo di lavoro e aggiungerlo di nuovo usando [Scale Out Manager](integration-services-ssis-scale-out-manager.md) oppure seguire i passaggi da 5.1 a 5.3 descritti di seguito:

5.1 Installare il certificato SSL client nell'archivio Radice del computer locale nel nodo di lavoro

5.2 Aggiornare il file di configurazione del servizio Scale Out Worker, \<unità\>:\Programmi\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config, nel nodo di lavoro. Aggiornare **MasterHttpsCertThumbprint** all'identificazione personale del nuovo certificato SSL.

5.3 Riavviare il servizio Scale Out Worker


## <a name="scale-out-worker-certificate"></a>Certificato di Scale Out Worker

Il certificato di Scale Out Worker viene generato automaticamente durante l'installazione di Scale Out Worker. 

### <a name="change-scale-out-worker-certificate"></a>Modificare il certificato di Scale Out Worker

Se si vuole modificare il certificato di Scale Out Worker, attenersi alla procedura seguente.

#### <a name="1-create-a-certificate"></a>1. Creare un certificato
Creare e installare un certificato con il comando seguente:
```dos
MakeCert.exe -n CN={worker machine name};CN={worker machine ip} SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
Esempio:
```dos
MakeCert.exe -n CN=WorkerMachine;CN=10.0.2.8 SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
#### <a name="2-install-the-client-certificate-to-the-root-store-of-local-machine-on-worker-node"></a>2. Installare il certificato client nell'archivio Radice del computer locale nel nodo di lavoro

#### <a name="3-give-service-access-to-the-certificate"></a>3. Consentire al servizio l'accesso al certificato
Eliminare il certificato precedente e consentire al servizio Scale Out Worker l'accesso al nuovo certificato con il comando seguente:
```dos
certmgr.exe /del /c /s /r localmachine My /n {CN of the old certificate}
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the new certificate} -a {the account running Scale Out Worker service}
```
Esempio:
```dos
certmgr.exe /del /c /s /r localmachine My /n WorkerMachine
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s WorkerMachine -a SSISScaleOutWorker140
```
#### <a name="4-update-scale-out-worker-configuration-file"></a>4. Aggiornare il file di configurazione di Scale Out Worker
Aggiornare il file di configurazione del servizio Scale Out Worker, \<unità\>:\Programmi\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config nel nodo del ruolo di lavoro. Aggiornare **WorkerHttpsCertThumbprint** all'identificazione personale del nuovo certificato.

#### <a name="5-install-the-client-certificate-to-the-root-store-of-local-machine-on-master-node"></a>5. Installare il certificato client nell'archivio Radice del computer locale nel nodo master

#### <a name="6-restart-scale-out-worker-service"></a>6. Riavviare il servizio Scale Out Worker
