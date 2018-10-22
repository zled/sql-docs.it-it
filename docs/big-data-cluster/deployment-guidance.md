---
title: Come distribuire cluster di Big Data di SQL Server in Kubernetes | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/08/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: f998c9f9df91f08d3a4e1877942b901ae5d96aeb
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460656"
---
# <a name="how-to-deploy-sql-server-big-data-cluster-on-kubernetes"></a>Come distribuire cluster di Big Data di SQL Server in Kubernetes

Cluster di SQL Server Big Data possono essere distribuiti come contenitori docker in un cluster Kubernetes. Questa è una panoramica dei passaggi di installazione e configurazione:

- Configurare un cluster Kubernetes in una singola VM, cluster di macchine virtuali o nel servizio contenitore di Azure
- Installare lo strumento di configurazione di cluster `mssqlctl` nel computer client
- Distribuire cluster di Big Data di SQL Server in un cluster Kubernetes

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="prereqs"></a> Prerequisiti di cluster Kubernetes

Cluster di Big Data di SQL Server richiede una versione minima versione 1.10 per Kubernetes, per i server e client. Per installare una versione specifica nel client kubectl, vedere [installare kubectl binari tramite curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl).  Le versioni più recenti di minikube e servizio contenitore di AZURE sono almeno 1.10. Per AKS dovrai usare `--kubernetes-version` parametro per specificare una versione diversa da quella predefinita.

> [!NOTE]
> Si noti che le versioni di Kubernetes client e il server devono essere-1 o + 1 versione secondaria. Per altre informazioni, vedere [Kubernetes supportato rilasci e componente inclinazione](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

## <a id="kubernetes"></a> Configurazione del cluster Kubernetes

Se si dispone già di un cluster Kubernetes che soddisfa di sopra dei prerequisiti, quindi è possibile andare direttamente al [passaggio di distribuzione](#deploy). In questa sezione si presuppone una conoscenza di base dei concetti relativi a Kubernetes.  Per informazioni dettagliate su Kubernetes, vedere la [documentazione di Kubernetes](https://kubernetes.io/docs/home).

È possibile scegliere di distribuire Kubernetes in uno dei tre modi:

| Distribuzione di Kubernetes in: | Description |
|---|---|
| **Minikube** | Un cluster Kubernetes a nodo singolo in una macchina virtuale. |
| **Servizi Kubernetes Azure (AKS)** | Un servizio di contenitore Kubernetes gestito in Azure. |
| **Più macchine virtuali** | Un cluster Kubernetes distribuito nelle macchine virtuali usando kubeadm |

Per istruzioni sulla configurazione di una di queste opzioni di cluster Kubernetes per cluster di Big Data di SQL Server, vedere uno degli articoli seguenti:

   - [Configurare Minikube](deploy-on-minikube.md)
   - [Configurare Kubernetes in Azure Kubernetes Service](deploy-on-aks.md)
   
> [!TIP]
> Per un esempio di script python che consente di distribuire cluster di big data sia servizio contenitore di AZURE e SQL Server, vedere [distribuire un cluster di big data in Azure Kubernetes Service (AKS) di SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a id="deploy"></a> Distribuire cluster di Big Data di SQL Server

Dopo aver configurato il cluster Kubernetes, è possibile procedere con la distribuzione per il cluster di Big Data di SQL Server. Per distribuire un cluster di big data con tutte le configurazioni predefinite per un ambiente di sviluppo/test, seguire le istruzioni riportate in questo articolo:

[Guida introduttiva: Distribuire SQL Server del Cluster di Big Data in Kubernetes](quickstart-big-data-cluster-deploy.md)

Se si desidera personalizzare la configurazione di cluster di big data, in base alle esigenze del carico di lavoro, seguire il successivo set di istruzioni.

## <a name="verify-kubernetes-configuration"></a>Verificare la configurazione di kubernetes

Eseguire il seguente comando di kubectl per visualizzare la configurazione del cluster. Verificare che tale kubectl fa riferimento il contesto del cluster corretto.

```bash
kubectl config view
```

## <a name="install-mssqlctl-cli-management-tool-for-sql-server-big-data-cluster"></a>Installare lo strumento di gestione dell'interfaccia della riga di mssqlctl per cluster di Big Data di SQL Server
`mssqlctl` è un'utilità della riga di comando scritta in Python che consente agli amministratori di cluster avviare e gestire i cluster di big data tramite le API REST. La versione di Python minima richiesta è v3.5. È inoltre necessario disporre `pip` che consente di scaricare e installare `mssqlctl` dello strumento. In un client Windows, è possibile scaricare il pacchetto di Python necessario [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Per python3.5.3 e versioni successive, pip3 viene installato anche quando si installa Python. Durante l'installazione è possibile selezionare non di aggiunta al percorso. È possibile trovare in cui che si trova il pip3 e aggiungerlo manualmente al percorso.
In Linux (WSL o Ubuntu client, ad esempio), questi comandi verranno installato l'ultima versione 3.5 di Python e pip:

```bash
sudo apt-get update
sudo apt-get install python3
sudo apt-get install python3-pip
sudo pip3 install --upgrade pip
```

> [!NOTE]
Se l'installazione di Python non è presente il `requests` pacchetto, è necessario installare `requests` usando `python -m pip install requests`. Se si dispone già di un `requests` pacchetto installato, assicurarsi di avere la versione più recente eseguendo `python -m pip install requests --upgrade`.

Eseguire il comando seguente per installare msqlctl:

```bash
pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl
```

## <a name="define-environment-variables"></a>Definire le variabili di ambiente

La configurazione del cluster può essere personalizzata usando un set di variabili di ambiente che vengono passati al `mssqlctl create cluster` comando. La maggior parte delle variabili di ambiente sono facoltativa con avalues predefinito come indicato di seguito. Si noti che le variabili di ambiente, ad esempio le credenziali che richiedono l'input dell'utente.

| Variabile di ambiente | Obbligatorio | Valore predefinito | Description |
|---|---|---|---|
| **ACCEPT_EULA** | Sì | N/D | Accettare il contratto di licenza di SQL Server (ad esempio, "Y").  |
| **CLUSTER_NAME** | Sì | N/D | Il nome dello spazio dei nomi Kubernetes per distribuire un cluster di Big Data a SQL Server. |
| **CLUSTER_PLATFORM** | Sì | N/D | La piattaforma che è distribuito il cluster Kubernetes. Può essere `aks`, `minikube`, `kubernetes`|
| **CLUSTER_COMPUTE_POOL_REPLICAS** | no | 1 | Il numero di repliche di pool di calcolo da compilare. In CTP2.0 solo con valori consentito è 1. |
| **CLUSTER_DATA_POOL_REPLICAS** | no | 2 | Il numero di dati del pool di repliche da compilare. |
| **CLUSTER_STORAGE_POOL_REPLICAS** | no | 2 | Il numero di repliche di pool di archiviazione da compilare. |
| **DOCKER_REGISTRY** | Sì | TBD | Il Registro di sistema privato in cui sono archiviate le immagini usate per distribuire il cluster. |
| **DOCKER_REPOSITORY** | Sì | TBD | Il repository privato all'interno del Registro di sistema precedente in cui sono archiviate le immagini.  È necessario per la durata dell'anteprima pubblica gestita. |
| **DOCKER_USERNAME** | Sì | N/D | Il nome utente per accedere alle immagini di contenitore nel caso in cui sono archiviati in un repository privato. È necessario per la durata dell'anteprima pubblica gestita. |
| **DOCKER_PASSWORD** | Sì | N/D | La password per accedere al repository privato precedente. È necessario per la durata dell'anteprima pubblica gestita.|
| **DOCKER_EMAIL** | Sì | N/D | Messaggio di posta elettronica associato al repository privato precedente. È necessario per la durata della fase di anteprima privata gestita. |
| **DOCKER_IMAGE_TAG** | no | più recente | L'etichetta utilizzata per contrassegnare le immagini. |
| **DOCKER_IMAGE_POLICY** | no | Always | Imporre sempre un'operazione pull delle immagini.  |
| **DOCKER_PRIVATE_REGISTRY** | Sì | 1 | Per l'intervallo di tempo dell'anteprima pubblica gestita, questo valore deve essere impostato su 1. |
| **CONTROLLER_USERNAME** | Sì | N/D | Il nome utente dell'amministratore cluster. |
| **CONTROLLER_PASSWORD** | Sì | N/D | La password dell'amministratore cluster. |
| **KNOX_PASSWORD** | Sì | N/D | La password per utente Knox. |
| **MSSQL_SA_PASSWORD** | Sì | N/D | La password dell'utente dell'amministratore di sistema per l'istanza master di SQL. |
| **USE_PERSISTENT_VOLUME** | no | true | `true` Per utilizzare attestazioni Volume permanente Kubernetes per l'archiviazione di pod.  `false` usare l'archiviazione temporanea host per l'archiviazione di pod. Vedere le [persistenza dei dati](concept-data-persistence.md) per altre informazioni. Se si distribuisce SQL Server del cluster di big data in minikube e USE_PERSISTENT_VOLUME = true, è necessario impostare il valore per `STORAGE_CLASS_NAME=standard`. |
| **STORAGE_CLASS_NAME** | no | predefiniti | Se `USE_PERSISTENT_VOLUME` è `true` viene indicato il nome della classe di archiviazione Kubernetes da usare. Vedere le [persistenza dei dati](concept-data-persistence.md) per altre informazioni. Si noti che se si distribuisce SQL Server del cluster in minikube dei big data, il nome predefinito della classe di archiviazione è diverso, che è necessario eseguirne l'override impostando `STORAGE_CLASS_NAME=standard`. |
| **MASTER_SQL_PORT** | no | 31433 | La porta TCP/IP che è in ascolto l'istanza SQL master nella rete pubblica. |
| **KNOX_PORT** | no | 30443 | Porta TCP/IP Knox Apache è in ascolto sulla rete pubblica. |
| **GRAFANA_PORT** | no | 30888 | Porta TCP/IP di Grafana con monitoraggio dell'applicazione è in ascolto sulla rete pubblica. |
| **KIBANA_PORT** | no | 30999 | La porta TCP/IP che è in ascolto l'applicazione di ricerca log di Kibana nella rete pubblica. |



> [!IMPORTANT]
>1. Per la durata della fase di anteprima privata limitata, le credenziali del registro Docker privato verranno fornite all'utente durante la valutazione di [registrazione EAP](https://aka.ms/eapsignup).
>1. Per un cluster locale compilato con kubeadm, il valore per la variabile di ambiente `CLUSTER_PLATFORM` è `kubernetes`. Inoltre, quando USE_PERSISTENT_STORAGE = true, è necessario pre-provisioning di una classe di archiviazione Kubernetes e passarlo tramite il STORAGE_CLASS_NAME.
>1. Verificare che a capo le password tra virgolette quando contiene caratteri speciali. È possibile impostare il MSSQL_SA_PASSWORD con qualsiasi nome desiderato, ma assicurarsi che questi sono sufficientemente complessi e non usare la `!`, `&` o `‘` caratteri. Si noti che i delimitatori tra virgolette doppie funzionano solo in comandi bash.
>1. Il nome del cluster deve essere solo alfanumerici caratteri minuscoli, senza spazi. Tutti Kubernetes gli elementi (contenitori, i POD, set prive di stato e servizi) per il cluster verranno creati in uno spazio dei nomi con lo stesso nome del cluster il nome specificato.
>1. Il **SA** account sia un amministratore di sistema nell'istanza Master di SQL Server che viene creato durante l'installazione. Dopo la creazione il contenitore di SQL Server, la variabile di ambiente MSSQL_SA_PASSWORD specificata diventa individuabile eseguendo echo MSSQL_SA_PASSWORD $ nel contenitore. Per motivi di sicurezza, modificare la password dell'amministratore di sistema in base alle procedure consigliate documentate [qui](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Impostare le variabili di ambiente necessarie per la distribuzione Aris cluster è diverso a seconda se si usano client Windows o Linux.  Scegliere i passaggi seguenti a seconda del sistema operativo in uso.

Inizializzare le variabili di ambiente seguente, sono necessari per distribuire il cluster:

### <a name="windows"></a>Windows

Usa una finestra CMD (non PowerShell), configurare le variabili di ambiente seguenti:

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=<minikube or aks or kubernetes>

SET CONTROLLER_USERNAME=<controller_admin_name – can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instances>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username>
SET DOCKER_PASSWORD=<your password>
SET DOCKER_EMAIL=<your Docker email, use same as username provided>
SET DOCKER_PRIVATE_REGISTRY="1"
```

In minikube, se USE_PERSISTENT_VOLUME = true (impostazione predefinita), è necessario anche il valore predefinito per la variabile di ambiente STORAGE_CLASS_NAME overide:
```
SET STORAGE_CLASS_NAME=standard
```

In alternativa, è possibile eliminare usando volumi permanenti in minikube:
```
SET USE_PERSISTENT_VOLUME=false
```
### <a name="linux"></a>Linux

Inizializzare le variabili di ambiente seguenti:

```bash
export ACCEPT_EULA=Y
export CLUSTER_PLATFORM=<minikube or aks or kubernetes>

export CONTROLLER_USERNAME=<controller_admin_name – can be anything>
export CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
export KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
export MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instances>

export DOCKER_REGISTRY=private-repo.microsoft.com
export DOCKER_REPOSITORY=mssql-private-preview
export DOCKER_USERNAME=<your username>
export DOCKER_PASSWORD=<your password>
export DOCKER_EMAIL=<your Docker email, use same as username provided>
export DOCKER_PRIVATE_REGISTRY="1"
```

In minikube, se USE_PERSISTENT_VOLUME = true (impostazione predefinita), è necessario anche il valore predefinito per la variabile di ambiente STORAGE_CLASS_NAME overide:
```
SET STORAGE_CLASS_NAME=standard
```

In alternativa, è possibile eliminare usando volumi permanenti in minikube:
```
SET USE_PERSISTENT_VOLUME=false
```
## <a name="deploy-sql-server-big-data-cluster"></a>Distribuire cluster di Big Data di SQL Server

L'API di creazione del cluster viene usato per inizializzare lo spazio dei nomi Kubernetes e distribuire tutti i POD delle applicazioni nello spazio dei nomi. Per distribuire cluster di Big Data di SQL Server nel cluster Kubernetes, eseguire il comando seguente:

```bash
mssqlctl create cluster <name of your cluster>
```

Durante il bootstrap del cluster, la finestra di comando del client verrà output lo stato della distribuzione. È anche possibile controllare lo stato della distribuzione eseguendo questi comandi in una finestra di comando diverse:

```bash
kubectl get all -n <name of your cluster>
kubectl get pods -n <name of your cluster>
kubectl get svc -n <name of your cluster>
```

È possibile visualizzare un stato e la configurazione per ogni pod più granulari eseguendo:
```bash
kubectl describe pod <pod name> -n <name of your cluster>
```

I pod Controller è in esecuzione, è possibile usare la scheda di distribuzione nel portale di amministrazione Cluster per monitorare la distribuzione.

## <a id="masterip"></a> Ottenere l'istanza di SQL Server Master e gli indirizzi IP del cluster di Big Data di SQL Server

Una volta completato lo script di distribuzione, è possibile ottenere l'indirizzo IP dell'istanza master di SQL Server mediante i passaggi descritti di seguito. Si userà questo indirizzo IP e porta numero 31433 per connettersi all'istanza master di SQL Server (ad esempio:  **\<ip-address\>, 31433**). Analogamente, per l'indirizzo IP del cluster di Big Data di SQL Server. Tutti gli endpoint del cluster sono illustrati nella scheda endpoint del servizio nel portale di amministrazione Cluster. È possibile usare il portale di amministrazione Cluster per monitorare la distribuzione. È possibile accedere al portale con l'esterno indirizzo IP e porta numero per il `service-proxy-lb` (ad esempio: **https://\<ip-address\>: 30777**). Le credenziali per accedere al portale di amministrazione sono i valori delle `CONTROLLER_USERNAME` e `CONTROLLER_PASSWORD` variabili di ambiente fornite sopra.

### <a name="aks"></a>SERVIZIO CONTENITORE DI AZURE

Se si usa servizio contenitore di AZURE, Azure fornisce il servizio di bilanciamento del carico di Azure. Eseguire il comando seguente:

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
kubectl get svc service-proxy-lb -n <name of your cluster>
```

Cercare il **External-IP** valore assegnato al servizio. Quindi, connettersi all'istanza master di SQL Server usando l'indirizzo IP alla porta 31433 (es:  **\<ip-address\>, 31433**) e ai Big Data di SQL Server del cluster usando l'indirizzo IP esterno per endpoint `service-security-lb` servizio. 

### <a name="minikube"></a>Minikube

Se si usa Minikube, è necessario eseguire il comando seguente per ottenere l'indirizzo IP che è necessario connettersi a. Oltre all'indirizzo IP, specificare la porta per l'endpoint a che è necessario connettersi. Per ottenere tutti gli endpoint di servizio per 

```bash
minikube ip
```

Indipendentemente dalla piattaforma si sta usando il cluster Kubernetes, per ottenere tutti gli endpoint del servizio distribuiti per il cluster, eseguire il comando seguente:
```bash
kubectl get svc -n <name of your cluster>
```

## <a name="next-steps"></a>Passaggi successivi

Dopo aver completato la distribuzione di Big Data di SQL Server del cluster di Kubernetes [installare gli strumenti dei big data](deploy-big-data-tools.md) e provare alcune delle nuove funzionalità e altre [come usare i notebook in fase di anteprima di SQL Server 2019](notebooks-guidance.md).
