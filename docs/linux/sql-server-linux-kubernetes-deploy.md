---
title: Distribuire SQL Server Always On gruppo di disponibilità nel Cluster Kubernetes
description: Questo articolo illustra i parametri per Kubernetes Always On di SQL Server requisiti di disponibilità gruppo operatore globali
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4d24cd2ab59e1a7959f5a8ac1c929ff2e5e8e54a
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049601"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-kubernetes-cluster"></a>Distribuire un Server SQL sempre sul gruppo di disponibilità nel Cluster Kubernetes

## <a name="requirements"></a>Requisiti

- Un cluster Kubernetes
- Kubernetes versione 1.11.0 o successiva
- Quattro o più nodi
- [kubectl](http://kubernetes.io/docs/tasks/tools/install-kubectl/).

  >[!NOTE]
  >È possibile usare qualsiasi tipo di cluster Kubernetes. Per creare un cluster Kubernetes in Azure Kubernetes Service (AKS), vedere [creare un cluster AKS](http://docs.microsoft.com/azure/aks/create-cluster.md).
  > Lo script seguente crea un cluster a quattro nodi Kubernetes in Azure.
  >```azure-cli
  az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version 1.11.1
  >```

## <a name="steps"></a>Passaggi

1. Configurare l'archiviazione

  Negli ambienti cloud come Azure, configurare [volumi permanenti](http://kubernetes.io/docs/concepts/storage/persistent-volumes/) per ogni istanza di SQL Server.

  Per creare volumi permanenti in Azure, vedere `pv.yaml` e `pvc.yaml` nelle [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/templates).

  Per creare lo spazio di archiviazione eseguire il comando seguente:

  ```azurecli
  kubectl apply -f <pv.yaml>
  ```

1. Creare i segreti Kubernetes per la password dell'amministratore di sistema e la chiave master.

  L'esempio seguente crea due segreti. `sapassword` è la password dell'amministratore di sistema e `masterkeypassword` è per la chiave master. Prima di eseguire questo script sostituisce `<MyC0mp13xP@55w04d!>` con password complesse diversa per ogni chiave privata.

   ```azurecli
   kubectl create secret generic sql-secrets --from-literal='sapassword=<MyC0mp13xP@55w04d!>' --from-literal='masterkeypassword=<MyC0mp13xP@55w04d!>'
   ```

1. Configurare e distribuire il manifesto dell'operatore di SQL Server.

  Copiare l'operatore di SQL Server `operator.yaml` del file da [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

  Il `operator.yaml` file è manifiest la distribuzione per l'operatore di Kubernetes.

  Per configurare il manifesto, aggiornare il `operator.yaml` file per l'ambiente.

  Applicare il manifesto per il cluster Kubernetes.

  ```azurecli
  kubectl apply -f operator.yaml
  ```

1. Distribuire la risorsa personalizzata di SQL Server.

  Copiare il manifesto di SQL Server `sqlserver.yaml` dal [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

  Applicare il manifesto per il cluster Kubernetes.

  ```azurecli
  kubectl apply -f sqlserver.yaml
  ```

Dopo aver distribuito il manifesto di SQL Server, l'operatore distribuisce le istanze di SQL Server come i POD in contenitori.

Al termine dell'esecuzione dello script, l'operatore di Kubernetes creerà lo spazio di archiviazione, le istanze di SQL Server, i servizi di bilanciamento di carico. È possibile monitorare la distribuzione con [dashboard di Kubernetes](http://docs.microsoft.com/azure/aks/kubernetes-dashboard).

Dopo che Kubernetes ha creato i contenitori di SQL Server completare i passaggi seguenti per aggiungere un database a gruppo di disponibilità:

1. [Connettere](sql-server-linux-kubernetes-connect.md) a un'istanza di SQL Server nel cluster.

1. Creazione di un database.

1. Eseguire un backup completo del database per avviare la catena di log.

1. Aggiungere il database al gruppo di disponibilità.

Viene creato il gruppo di disponibilità con seeding automatico in modo che SQL Server crea automaticamente le repliche secondarie.

## <a name="next-steps"></a>Passaggi successivi

[Connettersi al gruppo di disponibilità SQL Server in cluster Kubernetes](sql-server-linux-kubernetes-connect.md)

[Gestire il gruppo di disponibilità SQL Server in cluster Kubernetes](sql-server-linux-kubernetes-manage.md)

[Gruppo di disponibilità SQL Server in cluster Kubernetes](sql-server-ag-kubernetes.md)