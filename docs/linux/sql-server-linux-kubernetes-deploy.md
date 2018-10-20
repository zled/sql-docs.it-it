---
title: Distribuire SQL Server Always On gruppo di disponibilità nel Cluster Kubernetes
description: Questo articolo illustra i parametri per Kubernetes Always On di SQL Server requisiti di disponibilità gruppo operatore globali
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 10/02/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3d4a2786a795b20e9c2f943824027859230b2c85
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460466"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-kubernetes-cluster"></a>Distribuire un Server SQL sempre sul gruppo di disponibilità nel Cluster Kubernetes

Nell'esempio riportato in questo articolo consente di distribuire un gruppo di disponibilità Always On di SQL Server in un cluster Kubernetes con tre repliche. Le repliche secondarie sono in modalità con commit sincrono.

In Kubernetes la distribuzione include un operatore di SQL Server, i contenitori di SQL Server e carico di servizi di bilanciamento del carico. L'operatore gestisce automaticamente il gruppo di disponibilità. Questo articolo illustra come:

- Distribuire l'operatore, i contenitori di SQL Server e servizi di bilanciamento del carico
- Connettersi al gruppo di disponibilità con i servizi
- Aggiungere un database al gruppo di disponibilità

## <a name="requirements"></a>Requisiti

- Un cluster Kubernetes
- Kubernetes versione 1.11.0 o successiva
- Almeno tre nodi
- [kubectl](http://kubernetes.io/docs/tasks/tools/install-kubectl/).
- Accedere per il [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) repository github

  >[!NOTE]
  >È possibile usare qualsiasi tipo di cluster Kubernetes. Per creare un cluster Kubernetes in Azure Kubernetes Service (AKS), vedere [creare un cluster AKS](http://docs.microsoft.com/azure/aks/create-cluster).
  > Lo script seguente crea un cluster a quattro nodi Kubernetes in Azure.
  >```azure-cli
  az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version 1.11.3 --generate-ssh-keys
  >```

## <a name="deploy-the-operator-sql-server-containers-and-load-balancing-services"></a>Distribuire l'operatore, i contenitori di SQL Server e servizi di bilanciamento del carico

1. Creare un [dello spazio dei nomi](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/).

  Questo esempio usa uno spazio dei nomi denominato `ag1`. Eseguire il comando seguente per creare lo spazio dei nomi.

  ```azurecli
  kubectl create namespace ag1
  ```

  Tutti gli oggetti appartenenti a questa soluzione sono nel `ag1` dello spazio dei nomi.

1. Configurare e distribuire il manifesto dell'operatore di SQL Server.

  Copiare il Server SQL [ `operator.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml) file dalla [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

  Il `operator.yaml` file è il manifesto di distribuzione per l'operatore di Kubernetes.

  Applicare il manifesto per il cluster Kubernetes.

  ```azurecli
  kubectl apply -f operator.yaml --namespace ag1
  ```

1. Creazione di un segreto Kubernetes con le password per il `sa` account e la chiave master dell'istanza SQL Server.

  Creare il segreto con `kubectl`.
  
  L'esempio seguente crea un segreto denominato `sql-secrets` nella `ag1` dello spazio dei nomi. Il segreto archivia due password:
  
  - `sapassword` memorizza la password per il Server SQL `sa` account.
  - `masterkeypassword` memorizza la password utilizzata per creare la chiave master di SQL Server. 

  Copiare lo script al terminale. Sostituire ogni `<>` con una password complessa ed eseguire lo script per creare il segreto.

  >[!NOTE]
  >La password non è possibile usare `&`, o `` ` `` caratteri.

  ```azurecli
  kubectl create secret generic sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
  ```

1. Distribuire la risorsa personalizzata di SQL Server.

  Copiare il manifesto di SQL Server [ `sqlserver.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) dalla [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

  >[!NOTE]
  >Il `sqlserver.yaml` file descrive i contenitori SQL Server, le attestazioni di volume permanente, volumi permanenti e servizi di bilanciamento del carico necessarie per ogni istanza di SQL Server.

  Applicare il manifesto per il cluster Kubernetes.

  ```azurecli
  kubectl apply -f sqlserver.yaml --namespace ag1
  ```
  
  L'immagine seguente mostra l'applicazione corretta del `kubectl apply` per questo esempio.

  ![creare sqlservers](./media/sql-server-linux-kubernetes-deploy/create-sqlservers.png)

  Dopo aver applicato il manifesto di SQL Server, l'operatore consente di distribuire i contenitori di SQL Server.

  Kubernetes colloca i contenitori nel POD. Usare `kubectl get pods --namespace ag1` per visualizzare lo stato dei POD. L'immagine seguente mostra la distribuzione di esempio dopo il numero di POD di SQL Server viene distribuiti. 

  ![compilato POD](./media/sql-server-linux-kubernetes-deploy/builtpods.png)

### <a name="monitor-the-deployment"></a>Monitorare la distribuzione

È possibile usare [dashboard di Kubernetes con Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard) monitorare la distribuzione.

Usare `az aks browse` per avviare il dashboard. 

## <a name="connect-to-the-availability-group-with-the-services"></a>Connettersi al gruppo di disponibilità con i servizi

Il [ `ag-services.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) dalla [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) esempio descrive i servizi di bilanciamento del carico che possono connettersi a repliche del gruppo di disponibilità. 

- `ag1-primary` fornisce un endpoint per la connessione alla replica primaria.
- `ag1-secondary` fornisce un endpoint per la connessione a qualsiasi replica secondaria.

Quando si applica il file manifesto, Kubernetes crea i servizi di bilanciamento del carico per ogni tipo di replica. Il servizio di bilanciamento del carico include un indirizzo IP. Usare questo indirizzo IP per connettersi al tipo di replica che è necessario.

Per distribuire i servizi, eseguire il comando seguente.

```azurecli
kubectl apply -f ag-services.yaml --namespace ag1
```

Dopo aver distribuito i servizi, utilizzare `kubectl get services --namespace ag1` per identificare l'indirizzo IP per i servizi.

Con l'indirizzo IP, è possibile connettersi all'istanza di SQL Server che ospita ogni tipo di replica.

L'immagine seguente mostra:

- L'output dalla `kubectl get services` dello spazio dei nomi `ag1`.

 I servizi, i servizi di bilanciamento del carico che vengono creati per ogni contenitore di SQL Server. Usare questi indirizzi IP come endpoint per connettersi direttamente alle istanze di SQL Server nel cluster.

- Il `sqlcmd` connessione alla replica primaria, con la `sa` account tramite l'endpoint di bilanciamento del carico.

![connect](./media/sql-server-linux-kubernetes-deploy/connect.png)

## <a name="add-a-database-to-the-availability-group"></a>Aggiungere un database al gruppo di disponibilità

>[!NOTE]
>A questo punto, SQL Server Management Studio non è possibile aggiungere un database a un gruppo di disponibilità. Usare Transact-SQL.

Dopo che Kubernetes ha creato i contenitori di SQL Server, completare i passaggi seguenti per aggiungere un database a gruppo di disponibilità:

1. [Connettere](sql-server-linux-kubernetes-connect.md) a un'istanza di SQL Server nel cluster.

1. Creazione di un database.

  ```sql
  CREATE DATABASE [demodb]
  ```

1. Eseguire un backup completo del database per avviare la catena di log.

  ```sql
  USE MASTER
  GO
  BACKUP DATABASE [demodb] 
  TO DISK = N'/var/opt/mssql/data/demodb.bak'
  ```

1. Aggiungere il database al gruppo di disponibilità.

  ```sql
  ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [demodb]
  ```

Viene creato il gruppo di disponibilità con seeding automatico in modo che SQL Server crea automaticamente le repliche secondarie.

È possibile visualizzare lo stato del gruppo di disponibilità dal dashboard del gruppo di disponibilità di SQL Server Management Studio.

![dashboard](./media/sql-server-linux-kubernetes-deploy/dashboard.png)

## <a name="next-steps"></a>Passaggi successivi

[Connettersi al gruppo di disponibilità SQL Server in cluster Kubernetes](sql-server-linux-kubernetes-connect.md)

[Gestire il gruppo di disponibilità SQL Server in cluster Kubernetes](sql-server-linux-kubernetes-manage.md)

[Gruppo di disponibilità SQL Server in cluster Kubernetes](sql-server-ag-kubernetes.md)
