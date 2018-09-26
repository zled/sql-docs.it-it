---
title: Configurare un gruppo di disponibilità SQL Server Always On in contenitori Docker in Kubernetes | Microsoft Docs
description: Questa esercitazione illustra come distribuire SQL Server gruppo di disponibilità AlwaysOn con Kubernetes nel servizio contenitore di Azure.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: tutorial
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux,mvc
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6d21866f3f7004dff1ea86ca4f608580a79ab754
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049361"
---
# <a name="configure-a-sql-server-always-on-availability-group-on-docker-containers-in-kubernetes-with-azure-kubernetes-service-aks"></a>Configurare un gruppo di disponibilità SQL Server Always On in contenitori Docker in Kubernetes con Azure Kubernetes Service (AKS)

Questa esercitazione illustra come configurare un'istanza di SQL Server a disponibilità elevata in un contenitore nel servizio contenitore di AZURE. È anche possibile [distribuire un contenitore di SQL Server in Kubernetes](tutorial-sql-server-containers-kubernetes.md). Per confrontare le due diverse soluzioni di Kubernetes, vedere [disponibilità elevata per i contenitori di SQL Server](sql-server-linux-container-ha-overview.md).

In questa esercitazione, apprenderà come:  

> [!div class="checklist"]
> * Creare spazio di archiviazione
> * Distribuire l'operatore di SQL Server in un cluster Kubernetes 
> * Creare i segreti Kubernetes
> * Distribuire le istanze di SQL Server e gli agenti di integrità
> * Connettersi alla replica primaria
> * Aggiungere un database al gruppo di disponibilità

Questa esercitazione illustra l'architettura in [Azure Kubernetes Service (AKS)](http://docs.microsoft.com/azure/aks/). Se non hai una sottoscrizione di Azure, creare un [account gratuito](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) prima di iniziare.

Questo diagramma rappresenta la soluzione apportate in questa esercitazione:

![cluster kubernetes-gruppo di disponibilità](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

### <a name="deployment-methodology-for-kubernetes"></a>Metodologia di distribuzione per Kubernetes

Molte delle procedure in questo articolo creare un manifesto e quindi distribuire il manifesto per il cluster. Il manifesto è un file con estensione yaml con la descrizione degli oggetti Kubernetes distribuito.

I file con estensione yaml in questo esempio sono disponibili in [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability).

Gli oggetti includono archiviazione, operatori, i POD, contenitori e servizi.

## <a name="prerequisites"></a>Prerequisiti

* Familiarità con queste tecnologie

  * [Kubernetes](http://kubernetes.io) versione 1.8
  * [Azure Kubernetes Service (AKS)](http://docs.microsoft.com/azure/aks/)
  * [SQL Server in Docker](quickstart-install-connect-docker.md)
  * [Gruppo di disponibilità di SQL Server Always On](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

* Un cluster Kubernetes con quattro nodi.

  Per istruzioni, consultare [esercitazione: distribuire un cluster Azure Kubernetes Service (AKS)](http://docs.microsoft.com/azure/aks/tutorial-kubernetes-deploy-cluster).

* Installare [ `kubectl` ](https://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-deploy-cluster#install-the-kubectl-cli).

## <a name="configuration-and-deployment-procedures"></a>Procedure di configurazione e distribuzione

L'esercitazione mostrerà come applicare i file con estensione yaml per il cluster Kubernetes.

## <a name="create-the-secrets"></a>Creare i segreti

Per creare i segreti Kubernetes per archiviare le password per l'account SA di SQL Server e la chiave master di SQL Server, eseguire il comando seguente.

```azurecli
kubectl create secret generic sql-secrets --from-literal=sapassword="MyC0m9l&xP@ssw0rd" --from-literal=masterkeypassword="MyC0m9l&xP@ssw0rd2"
```

In un ambiente di produzione usare una password complessa diversi.

## <a name="deploy-the-operator"></a>Distribuire l'operatore

Un operatore di Kubernetes distribuisce le istanze di SQL Server e della configurazione del gruppo di disponibilità nel cluster Kubernetes. 

Vedere un esempio di operatori in [`operator.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml)

Scaricare `operator.yaml` da [sql-server-samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/)

Distribuire l'operatore come replica di una distribuzione di Kubernetes.

Per distribuire l'operatore:

Distribuire con l'operatore di `kubectl apply` comando.

```azurecli
kubectl apply -f operator.yaml
```

## <a name="create-the-sql-server-ag-deployment"></a>Creare la distribuzione del gruppo di disponibilità di SQL Server

Il passaggio successivo consente di creare istanze di SQL Server e il gruppo di disponibilità in una distribuzione di Kubernetes. Dopo aver applicato la distribuzione nel cluster, l'operatore distribuirà le istanze di SQL Server come contenitori Docker. Questa distribuzione provocherà tre StatefulSets con un pod. Ogni pod includerà due contenitori:

* Istanza di SQL Server in base il `mssql-server` immagine
* Supervisore a disponibilità elevata

Inoltre, la distribuzione viene descritto un servizio di bilanciamento del carico per il listener del gruppo di disponibilità

Per distribuire mssql-server:

1. Copia [sqlserver.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) nel computer.
2. Aggiornamento `sqlserver.yaml` per l'ambiente.


Per distribuire le istanze di SQL Server e creare il gruppo di disponibilità, eseguire il comando seguente.

```azurecli
kubectl apply -f sqlserver.yaml
```

## <a name="deploy-ag-services"></a>Servizi di distribuzione del gruppo di disponibilità

Creare servizi di bilanciamento carico per le chiamate dirette alle repliche del gruppo di disponibilità nel cluster Kubernetes.

[gruppo di disponibilità-services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) crea quattro servizi.

* AG1 primario si connette alla replica primaria.
* AG1-secondario-sincronizzazione si connette a una replica secondaria asincrona.
* AG1-secondario-async si connette a una replica secondaria asincrona.
* AG1-secondario-config si connette a una replica di sola configurazione. 

  >[!NOTE]
  >Questi servizi di bilanciamento di carico sono forniti come esempi. In questa esercitazione non replica di sola configurazione.


Distribuire i servizi di bilanciamento di carico in modo che sia possibile connettersi al gruppo di disponibilità.

Per distribuire i servizi, eseguire il comando seguente.

```azurecli
kubectl apply -f ag-services.yaml
```

### <a name="monitor-the-deployment"></a>Monitorare la distribuzione

È possibile usare [dashboard di Kubernetes con Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/kubernetes-dashboard) monitorare la distribuzione. 

Usare `az aks browse` per avviare il dashboard. 

Dopo la distribuzione, può essere aggiornato solo gruppo di disponibilità appartenenza elenco e post-inizializzazione script T-SQL. Non è possibile aggiornare le altre proprietà: la risorsa deve essere eliminata e ricreata. Le credenziali per gli utenti generato automaticamente possono essere ruotati utilizzando un `mssql-server-k8s-rotate-creds` processo.

## <a name="connect-to-the-sql-server-instance-hosting-the-primary-replica"></a>Connettersi all'istanza di SQL Server che ospita la replica primaria

Il `ag-services.yaml` descrive il nome di un servizio Kubernetes `ag1-primary`. `ag1-primary` Crea un servizio di bilanciamento del carico di Azure che fanno riferimento l'istanza di SQL Server che ospita la replica primaria. Usare l'indirizzo IP esterno del servizio come server di destinazione `sa` come account e la password creata in precedenza nel `mssql secret` la password.

Usare `kubectl get services` per ottenere questo indirizzo IP.

Esempio:

![Ottenere l'esempio di servizio](media\tutorial-sql-server-ag-containers-kubernetes\KubernetesGetServices.png)

Nell'immagine precedente, `ag1-primary` servizio dispone di un indirizzo IP esterno di `104.42-50.138`. 

Per connettersi a SQL Server con l'autenticazione di SQL, usare il `sa` account, il valore per `sapassword` dal segreto creato e questo indirizzo IP.

Esempio:

```cmd
sqlcmd -S 104.42.50.138 -U sa -P "MyC0m9l&xP@ssw0rd"
```

![La connessione con sqlcmd](./media/tutorial-sql-server-ag-containers-kubernetes/sqlcmdConnect.png)

È anche possibile connettersi con [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md).

Per verificare la connessione, per l'istanza di SQL Server che ospita la replica primaria eseguire la query seguente:

```sql
SELECT @@SERVERNAME;
```

La query restituisce il nome dell'istanza di SQL Server che ospita la replica primaria.

A questo punto, il cluster Kubernetes dispone di tre istanze di SQL Server in contenitori docker. Un gruppo di disponibilità si estende su tutte le tre istanze di SQL Server, ma non sono database nel gruppo di disponibilità. Il passaggio successivo consiste nell'aggiungere un database al gruppo di disponibilità.

## <a name="add-a-database-to-the-availability-group"></a>Aggiungere un database al gruppo di disponibilità

Per aggiungere un database al gruppo di disponibilità:

1. Creazione di un database

  ```sql
  CREATE DATABASE [DemoDB]
  ```

1. Eseguire un backup del database per avviare la catena di log delle transazioni completo

  ```sql
  BACKUP DATABASE [DemoDB] 
  TO  DISK = N'/var/opt/mssql/data/DemoDB.bak' 
    WITH NOFORMAT, 
    NOINIT,  
    NAME = N'DemoDB-Full Database Backup', 
    SKIP, 
    NOREWIND, 
    NOUNLOAD,  
    STATS = 10;
  GO
  ```

1. Aggiungere il database al gruppo di disponibilità

  ```sql
  ALTER AVAILABILITY GROUP ag1 ADD DATABASE [DemoDB]; 
  ```

La replica viene configurata automaticamente con la modalità di seeding automatico in modo che il gruppo di disponibilità esegue il seeding il database su repliche secondarie.

In SQL Server Management Studio, è possibile connettersi alla replica primaria e visualizzare il gruppo di disponibilità nel dashboard.

L'esempio seguente mostra il gruppo di disponibilità con repliche in tre nodi configurati nel dashboard.

![Dashboard di AG1](./media/tutorial-sql-server-ag-containers-kubernetes/ssms_AG1.png)

## <a name="verify-failure-and-recovery"></a>Verificare l'errore e il ripristino

Per verificare il failover e il rilevamento degli errori è possibile eliminare il pod che ospita la replica primaria. Kubernetes verranno sceglie una nuova replica primaria e reindirizzare il listener. Quindi verrà ricreato il pod eliminato. 

Per illustrare questo processo, procedere come segue:

1. Elencare i pod in esecuzione SQL Server.

   ```azurecli
   kubectl get pods
   ```

2. Identificare il pod che eseguono la replica primaria.

   Una connessione alla replica primaria usando l'indirizzo IP e query esterne `@@servername` oppure usare `kubectl` per ottenere il pod appropriato. Questo comando restituirà il nome del pod che include il contenitore che esegue la replica primaria del gruppo di disponibilità:

   ```azurecli
   kubectl get pods --selector="role.ag.mssql.microsoft.com/ag1"="primary" --output=jsonpath={.items..metadata.name}
   ```

3. Eliminare il pod.

   ```azurecli
   kubectl delete pod <podName>
   ```

Sostituire `<podName>` con il valore restituito nel passaggio precedente per nome del pod. 

Kubernetes automaticamente viene eseguito in una delle repliche secondarie sincronizzazione disponibili, nonché vengono ricreate nel pod eliminato.

## <a name="clean-up-resources"></a>Pulire le risorse

Quando non sono più necessari, eliminare il gruppo di risorse e tutte le risorse correlate. Eseguire il comando seguente:
>[!WARNING]
>Questo comando elimina completamente tutti gli elementi nel gruppo di risorse. Nessuno dei componenti del cluster Kubernetes saranno disponibili dopo aver eliminato il gruppo di risorse.

```azurecli
az group delete --name <MyResourceGroup>
```

Per eseguire il comando precedente, sostituire `<MyResourceGroup>` con il nome del gruppo di risorse. 

Azure consente di eliminare il gruppo di risorse.

## <a name="summary"></a>Riepilogo

In questa esercitazione si è appreso come:  

> [!div class="checklist"]
> * Creare spazio di archiviazione
> * Distribuire l'operatore di SQL Server in un cluster Kubernetes 
> * Creare i segreti Kubernetes
> * Distribuire le istanze di SQL Server e gli agenti di integrità
> * Connettersi alla replica primaria
> * Aggiungere un database al gruppo di disponibilità

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
>[Introduzione a Kubernetes](http://docs.microsoft.com/azure/aks/intro-kubernetes)
>[gestire SQL Server in Kubernetes](sql-server-linux-kubernetes-manage.md)