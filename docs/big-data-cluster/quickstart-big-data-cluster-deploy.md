---
title: Distribuire il cluster di big data di SQL Server | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: quickstart
ms.prod: sql
ms.openlocfilehash: 5781b3acfd2262b3a3be540abb331839dfcc56c6
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120458"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Guida introduttiva: Distribuire il cluster di big data di SQL Server in Azure Kubernetes Service (AKS)

In questa Guida introduttiva, si installerà il cluster di big data di SQL Server nel servizio contenitore di AZURE in una configurazione predefinita adatta per gli ambienti di sviluppo/test. Oltre all'istanza di SQL Master, il cluster includerà istanza di un calcolo del pool, istanza del pool di dati e due istanze del pool di archiviazione. I dati verranno mantenuti con volumi permanenti Kubernetes sono a provisioning all'inizio di classi di archiviazione predefinito AKS. Nel [Guida alla distribuzione](deployment-guidance.md) argomento è possibile trovare un set di variabili di ambiente che è possibile usare per personalizzare ulteriormente la configurazione.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>Prerequisiti

Questa Guida introduttiva richiede che sia già stato configurato un cluster AKS con una versione minima versione 1.10. Per altre informazioni, vedere la [distribuire nel servizio contenitore di AZURE](deploy-on-aks.md) Guida.

Nel computer in uso per eseguire i comandi per installare il cluster di big data di SQL Server, è necessario installare [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/). Cluster di big data di SQL Server richiede almeno la versione 1.10 per Kubernetes, per i server e client (kubectl). Per installare kubectl, vedere [installare kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). 

Per installare il `mssqlctl` strumento della riga di comando per gestire i dati di grandi dimensioni di SQL Server del cluster nel computer client, è necessario prima installare [Python](https://www.python.org/downloads/) v3.0 versione minima e [pip3](https://pip.pypa.io/en/stable/installing/). Si noti che pip sia già installato se si usa una versione di Python di almeno 3.4 scaricato dal [python.org](https://www.python.org/).

Se l'installazione di Python non è presente il `requests` pacchetto, è necessario installare `requests` usando `python -m pip install requests`. Se si dispone già di un `requests` pacchetto di aggiornamento alla versione più recente usando `python -m pip install requests --upgrade`.

## <a name="verify-aks-configuration"></a>Verificare la configurazione di servizio contenitore di AZURE

Dopo aver creato il cluster AKS distribuita, è possibile eseguire il seguente comando di kubectl per visualizzare la configurazione del cluster. Verificare che tale kubectl fa riferimento il contesto del cluster corretto.

```bash
kubectl config view
```

## <a name="install-mssqlctl-cli-management-tool"></a>Installare lo strumento di gestione dell'interfaccia della riga mssqlctl

Eseguire il seguente comando per installare `mssqlctl` tool nel computer client. Comando funziona da un Windows e un client Linux, ma assicurarsi che viene eseguita da una finestra di comando che viene eseguito con privilegi amministrativi in Windows o con prefisso `sudo` in Linux:

```
pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl  
```

## <a name="define-environment-variables"></a>Definire le variabili di ambiente

Impostare le variabili di ambiente necessarie per la distribuzione di cluster di big data leggermente diverso a seconda se si usano client Windows o Linux/macOS.  Scegliere i passaggi seguenti a seconda del sistema operativo in uso.

Prima di continuare, tenere presenti le linee guida seguenti:

- Verificare che a capo le password tra virgolette quando contiene caratteri speciali. Si noti che i delimitatori tra virgolette doppie funzionano solo in comandi bash.
- È possibile impostare le variabili di ambiente della password con qualsiasi nome desiderato, ma assicurarsi che questi sono sufficientemente complessi e non usare la `!`, `&`, o `‘` caratteri.
- Per la versione CTP 2.0, non modificare le porte predefinite.
- Il **SA** account sia un amministratore di sistema nell'istanza Master di SQL Server che viene creato durante l'installazione. Dopo la creazione il contenitore di SQL Server, la variabile di ambiente MSSQL_SA_PASSWORD specificata diventa individuabile eseguendo echo MSSQL_SA_PASSWORD $ nel contenitore. Per motivi di sicurezza, modificare la password dell'amministratore di sistema in base alle procedure consigliate documentate [qui](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Inizializzare le variabili di ambiente seguenti.  Sono necessari per distribuire un cluster di big data:

### <a name="windows"></a>Windows

Usa una finestra CMD (non PowerShell), configurare le variabili di ambiente seguenti:

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=aks

SET CONTROLLER_USERNAME=<controller_admin_name – can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username, credentials provided by Microsoft>
SET DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
SET DOCKER_EMAIL=<your Docker email, use the username provided by Microsoft>
SET DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="linuxmacos"></a>Linux/macOS

Inizializzare le variabili di ambiente seguenti:

```bash
export ACCEPT_EULA=Y
export CLUSTER_PLATFORM=aks

export CONTROLLER_USERNAME=<controller_admin_name – can be anything>
export CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
export KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
export MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

export DOCKER_REGISTRY=private-repo.microsoft.com
export DOCKER_REPOSITORY=mssql-private-preview
export DOCKER_USERNAME=<your username, credentials provided by Microsoft>
export DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
export DOCKER_EMAIL=<your Docker email, use the username provided by Microsoft>
export DOCKER_PRIVATE_REGISTRY="1"
```

> [!NOTE]
> Durante l'anteprima pubblica limitata, le credenziali di Docker per scaricare le immagini del cluster di Big Data di SQL Server sono fornite a ogni cliente da Microsoft. Per richiedere l'accesso, registrare [qui](https://aka.ms/eapsignup)e specificare l'interesse dimostrato per provare i cluster di big data di SQL Server.

## <a name="deploy-a-big-data-cluster"></a>Distribuire un cluster di big data

Per distribuire un cluster di big data 2019 CTP 2.0 di SQL Server nel cluster Kubernetes, eseguire il comando seguente:

```bash
mssqlctl create cluster <name of your cluster>
```

> [!NOTE]
> Il nome del cluster deve essere solo alfanumerici caratteri minuscoli, senza spazi. Tutti gli artefatti di Kubernetes per il cluster di big data verranno creati in uno spazio dei nomi con lo stesso nome del cluster il nome specificato.


La finestra di comando restituirà lo stato della distribuzione. È anche possibile controllare lo stato della distribuzione eseguendo questi comandi in una finestra di comando diverse:

```bash
kubectl get all -n <name of your cluster>
kubectl get pods -n <name of your cluster>
kubectl get svc -n <name of your cluster>
```

È possibile visualizzare un stato e la configurazione per ogni pod più granulari eseguendo:
```bash
kubectl describe pod <pod name> -n <name of your cluster>
```

Il pod Controller è in esecuzione, è possibile utilizzare il portale di amministrazione Cluster per monitorare la distribuzione. È possibile accedere al portale con l'esterno indirizzo IP e porta numero per il `service-proxy-lb` (ad esempio: **https://\<ip-address\>: 30777**). Le credenziali per accedere al portale di amministrazione sono i valori delle `CONTROLLER_USERNAME` e `CONTROLLER_PASSWORD` variabili di ambiente fornite sopra.

È possibile ottenere l'indirizzo IP del servizio servizio-proxy-lb eseguendo questo comando in una finestra bash o cmd:

```bash
kubectl get svc service-proxy-lb -n <name of your cluster>
```

> [!NOTE]
> Si verrà visualizzato un avviso di sicurezza all'accesso alla pagina web poiché si sta usando i certificati SSL generati automaticamente. Nelle future versioni, Microsoft fornirà la possibilità di fornire i propri certificati firmati.
 

## <a name="connect-to-the-big-data-cluster"></a>Connettersi al cluster di big data

Dopo che lo script di distribuzione è stata completata, è possibile ottenere l'indirizzo IP dell'istanza master di SQL Server e i punti finali Spark o HDFS usando i passaggi descritti di seguito. Tutti gli endpoint del cluster vengono visualizzati nella sezione nel portale di amministrazione Cluster anche per semplificarne la consultazione all'endpoint del servizio.

Azure offre il servizio di bilanciamento del carico di Azure al servizio contenitore di AZURE. Eseguire il seguente comando in una finestra di comando o la finestra di bash:

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
```

Cercare il **External-IP** valore assegnato ai servizi. Connettersi all'istanza master di SQL Server usando l'indirizzo IP per il `service-master-pool-lb` alla porta 31433 (es:  **\<ip-address\>, 31433**) e per l'endpoint del cluster SQL Server i big data usando l'indirizzo IP esterno per il `service-security-lb` servizio.   Che i big data cluster punto finale è che consente di interagire con HDFS e inviare processi Spark tramite Knox.

## <a name="next-steps"></a>Passaggi successivi

Ora che viene distribuito il cluster di big data di SQL Server, provare alcune delle nuove funzionalità:

> [!div class="nextstepaction"]
> [Come usare i notebook in fase di anteprima di SQL Server 2019](notebooks-guidance.md)
