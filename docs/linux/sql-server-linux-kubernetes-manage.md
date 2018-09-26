---
title: Gestire un SQL Server Always On gruppo di disponibilità Kubernetes
description: Questo articolo illustra come gestire un SQL Server gruppo di disponibilità AlwaysOn in Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 078149ff8d9c9c81ac8db95862bf685ca66fbe36
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049351"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>Gestire SQL Server Always On Kubernetes gruppo di disponibilità

Per gestire un gruppo di disponibilità AlwaysOn in Kubernetes, creare un manifesto e applicarlo al cluster. Il manifesto è un `.yaml` file.  

Gli esempi in questo articolo si applicano a tutti i cluster Kubernetes. Gli scenari in questi esempi vengono eseguiti in un cluster in Azure Kubernetes Service.

Vedere un esempio del della distribuzione end-to-end nel [in questa esercitazione](tutorial-sql-server-ag-kubernetes.md).

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>Eseguire il failover: gruppo di disponibilità SQL Server in Kubernetes

Per eseguire il failover una replica primaria del gruppo disponibilità in un altro nodo in Kubernetes, usare un processo. Questo articolo identifica le variabili di ambiente per questo processo.

L'esempio seguente di un file manifesto viene descritto un processo per eseguire manualmente il failover del processo per un gruppo di disponibilità su una replica di Kubernetes. Copia il contenuto dell'esempio in un nuovo file denominato `failover.yaml`.

[failover.yaml](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/templates/failover.yaml)

Per distribuire il processo, usare `Kubectl`.

```azurecli
kubectl apply -f failover.yaml
```

Quando si applica il file manifesto, Kubernetes esegue il processo. Quando si esegue il processo, il Supervisore sceglie un coordinatore nuovo e sposta la replica primaria per l'istanza di SQL Server del leader.

Dopo aver eseguito il processo, eliminarlo. L'oggetto processo in Kubernetes rimane dopo il completamento, quindi è possibile visualizzare lo stato. È necessario eliminare manualmente i processi precedenti dopo avere stabilito il relativo stato. L'eliminazione del processo elimina anche i log di Kubernetes. Se non si elimina il processo, i processi di failover future avrà esito negativo a meno che non si modifica il nome del processo e il selettore di pod. Per altre informazioni, vedere [- i processi eseguiti fino al completamento](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/).

## <a name="rotate-credentials"></a>Ruotare le credenziali

Ruotare le credenziali per aggiornare l'amministratore del servizio e la chiave master.

Copia il [creds.yaml ruotare](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script) usare in locale `kubectl` per applicarlo al cluster.

```azurecli
kubectl apply -f rotate-creds.yaml
```

## <a name="next-steps"></a>Passaggi successivi

[Accedere al dashboard di Kubernetes con Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[Gruppo di disponibilità SQL Server in cluster Kubernetes](sql-server-ag-kubernetes.md)