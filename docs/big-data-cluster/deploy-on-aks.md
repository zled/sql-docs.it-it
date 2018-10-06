---
title: Configurare Azure Kubernetes Service per le distribuzioni di SQL Server 2019 CTP 2.0 | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: ea1ab30f9b3b8ef77834a56b059b2a56de4467b5
ms.sourcegitcommit: 448106b618fe243e418bbfc3daae7aee8d8553d2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48796759"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-ctp-20"></a>Configurare Azure Kubernetes Service per SQL Server 2019 CTP 2.0

Azure Kubernetes Service (AKS) rende più semplice creare, configurare e gestire un cluster di macchine virtuali che sono preconfigurate con un cluster Kubernetes per eseguire applicazioni in contenitori. 

In questo modo è possibile usare le competenze esistenti o disegnare su un consistente e crescente bagaglio di competenze della community, distribuire e gestire le applicazioni basate su contenitore in Microsoft Azure.

Questo articolo descrive i passaggi per la distribuzione di Kubernetes nel servizio contenitore di AZURE tramite la CLI di Azure. Se non hai una sottoscrizione di Azure, creare un account gratuito prima di iniziare.

## <a name="prerequisites"></a>Prerequisiti

- Per un ambiente del servizio contenitore di AZURE, il requisito minimo di macchine Virtuali è almeno due macchine virtuali dell'agente (oltre a master) di una dimensione minima Standard_DS3_V2. Risorse minime necessarie per ogni macchina virtuale sono 4 CPU e 14 GB di memoria.

- In questa sezione è necessario che sia in esecuzione la CLI di Azure versione 2.0.4 o versioni successive. Se è necessario installare o eseguire l'aggiornamento, vedere [installare Azure CLI 2.0](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli). Eseguire `az --version` per trovare la versione, se necessario.

- Installare [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/). Cluster di Big Data di SQL Server richiede qualsiasi versione secondaria all'interno dell'intervallo di 1.10 versione per Kubernetes, per i server e client. Per installare una versione specifica nel client kubectl, vedere [installare kubectl binari tramite curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). Per AKS dovrai usare `--kubernetes-version` parametro per specificare una versione diversa da quella predefinita. Si noti che l'intervallo di tempo versione CTP2.0, servizio contenitore di AZURE supporta solo le versioni 1.10.7 e 1.10.8. 


> [!NOTE]
Si noti che la versione del client/server inclinare vale a dire supportato è + /-1 versione secondaria. La documentazione di Kubernetes indicato che "un client deve essere asimmetriche non più di una versione secondaria dal server master, ma può causare il master da una versione secondaria. Ad esempio, un master v1.3 dovrebbe funzionare con la versione 1.1, versione 1.2 e nodi v1.3 e dovrebbe funzionare con v1.2 v1.3 e i client versione 1.4." Per altre informazioni, vedere [Kubernetes supportato rilasci e componente inclinazione](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

Si noti inoltre che `az aks kubernetes install-cli` installerà il client kubectl con una versione inferiore che il 1.10 obbligatorio. Seguire le istruzioni per installare la versione corretta del client kubectl di sopra.

## <a name="create-a-resource-group"></a>Creare un gruppo di risorse

Un gruppo di risorse di Azure è un gruppo logico in Azure le risorse vengono distribuite e gestite. Questa procedura, accede ad Azure e crea un gruppo di risorse per il cluster AKS.

> [!TIP]
> Se si usa Windows, usare PowerShell per il resto dei passaggi.

1. Al prompt dei comandi, eseguire il comando seguente e seguire le istruzioni per eseguire l'accesso alla sottoscrizione di Azure:

    ```bash
    az login
    ```

1. Se si hanno più sottoscrizioni, è possibile visualizzare tutte le sottoscrizioni eseguendo il comando seguente:

   ```bash
   az account list
   ```

1. Se si desidera modificare una sottoscrizione diversa è possibile eseguire questo comando:

   ```bash
   az account set --subscription <subscription id>
   ```

1. Creare un gruppo di risorse con il **creare il gruppo di az** comando. L'esempio seguente crea un gruppo di risorse denominato `sqlbigdatagroup` nella `westus2` posizione.

   ```bash
   az group create --name sqlbigdatagroup --location westus2
   ```

## <a name="create-a-kubernetes-cluster"></a>Creare un cluster Kubernetes

1. Creare un cluster Kubernetes nel servizio contenitore di AZURE con il [az aks create](https://docs.microsoft.com/cli/azure/aks) comando. L'esempio seguente crea un cluster Kubernetes denominato *kubcluster* con un Linux nodo master e due nodi agente Linux. Assicurarsi di che creare il cluster AKS nello stesso gruppo di risorse usato nelle sezioni precedenti.

    ```bash
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_DS3_v2 \
    --node-count 2 \
    --kubernetes-version 1.10.7
    ```

    È possibile aumentare o ridurre il numero di agenti predefinito aggiungendo `--node-count <n>` per il az aks create comando dove `<n>` è il numero di nodi agente che si desidera avere.

    Dopo alcuni minuti, il comando viene completato e restituisce le informazioni in formato JSON sul cluster.

1. Salvare l'output JSON ottenuto dal comando precedente per un uso successivo.

## <a name="connect-to-the-cluster"></a>Connettersi al cluster

1. Per configurare kubectl per la connessione al cluster Kubernetes, eseguire la [az aks get-credentials](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) comando. Questo passaggio Scarica credenziali e consente di configurare l'interfaccia della riga di comando per usarli kubectl.

   ```bash
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. Per verificare la connessione al cluster, usare il [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) comando per restituire un elenco dei nodi del cluster.  L'esempio seguente mostra l'output se fosse necessario 1 master e 3 nodi agente.

   ```bash
   kubectl get nodes
   ```

## <a name="next-steps"></a>Passaggi successivi

I passaggi descritti in questo articolo è configurato un cluster Kubernetes nel servizio contenitore di AZURE. Il passaggio successivo consiste nel distribuire SQL Server 2019 Big Data per il cluster.

[Distribuire cluster di SQL Server 2019 Big Data in Kubernetes](quickstart-big-data-cluster-deploy.md)
