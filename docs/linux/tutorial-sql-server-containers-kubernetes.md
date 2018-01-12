---
title: "Configurare il contenitore di SQL Server in Kubernetes per la disponibilità elevata | Documenti Microsoft"
description: "In questa esercitazione viene illustrato come distribuire una soluzione di disponibilità elevata di SQL Server con Kubernetes sul servizio contenitore di Azure."
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 01/10/2018
ms.topic: tutorial
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: mvc
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 5055a5956ce83dadae3cef13f0855db02a61d01b
ms.sourcegitcommit: 06131936f725a49c1364bfcc2fccac844d20ee4d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="configure-sql-server-container-in-kubernetes-for-high-availability"></a>Configurare il contenitore di SQL Server in Kubernetes per la disponibilità elevata

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Seguire questo articolo per configurare un'istanza di SQL Server nel servizio contenitore di Azure (AKS) Kubernetes con archivio permanente per la disponibilità elevata. La soluzione fornisce resilienza. Se l'istanza di SQL Server non riesce, Kubernetes ricrea automaticamente in un nuovo pod. AKS fornisce resilienza errore Kubernetes del nodo. 

Questa esercitazione viene illustrato come configurare un'istanza di SQL Server a disponibilità elevata in contenitori usando AKS. 

> [!div class="checklist"]
> * Password dell'account SA di creazione
> * Creare spazio di archiviazione
> * Creare una distribuzione
> * La connessione con SQL Server Management Studio (SSMS)
> * Verificare l'errore e ripristino

### <a name="ha-solution-using-kubernetes-running-in-azure-container-service"></a>Soluzione a disponibilità elevata utilizzando Kubernetes in esecuzione nel servizio contenitore di Azure

Kubernetes 1.6 + dispone del supporto per [classi di archiviazione](http://kubernetes.io/docs/concepts/storage/storage-classes/), [permanente attestazioni Volume](http://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)e [driver volume del disco di Azure](http://github.com/Azure/azurefile-dockervolumedriver). È possibile creare e gestire le istanze di SQL Server in modo nativo nel Kubernetes. Nell'esempio riportato in questo articolo viene illustrato come creare un [distribuzione](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) per ottenere una configurazione a disponibilità elevata come cluster di failover di un disco condiviso. In questa configurazione, Kubernetes svolgerà il ruolo dell'agente di orchestrazione del cluster. Quando un'istanza di SQL Server in un contenitore ha esito negativo, l'agente di orchestrazione avvio di un'altra istanza del contenitore che collega alla stessa archiviazione permanente.

![Cluster di Server SQL Kubernetes](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

Nel diagramma precedente, `mssql-server` è un contenitore in un [pod](http://kubernetes.io/docs/concepts/workloads/pods/pod/). Kubernetes gestisce le risorse del cluster. Oggetto [set di repliche](http://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) assicura che l'unità viene recuperato automaticamente dopo un errore di nodo. Applicazioni di connettono al servizio. In questo caso, il servizio rappresenta un bilanciamento del carico che ospita un indirizzo IP che rimarrà invariata dopo un errore dei `mssql-server`.

Nel diagramma seguente, il `mssql-server` contenitore non è riuscita. Come agente di orchestrazione, Kubernetes garantisce il corretto numero di istanze integre nella replica di impostarla e avvia un nuovo contenitore in base alla configurazione. L'agente di orchestrazione viene avviato un nuovo pod nello stesso nodo, e `mssql-server` si riconnette alla stessa archiviazione permanente. Il servizio si connette per la ricreata `mssql-server`.

![Cluster di Server SQL Kubernetes dopo](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-pod-fail.png)

Nel diagramma seguente, il nodo che ospita il `mssql-server` contenitore non è riuscita. L'agente di orchestrazione avvia il nuovo pod su un nodo diverso, e `mssql-server` si riconnette alla stessa archiviazione permanente. Il servizio si connette per la ricreata `mssql-server`.

![Cluster di Server SQL Kubernetes dopo](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-node-fail.png)

## <a name="prerequisites"></a>Prerequisiti

* **Kubernetes cluster**
   - L'esercitazione è necessario un cluster Kubernetes. Utilizza la procedura [kubectl](https://kubernetes.io/docs/user-guide/kubectl/), per gestire il cluster. 

   - È possibile seguire le istruzioni in [distribuire un cluster del servizio contenitore di Azure (AKS)](http://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-deploy-cluster) per creare e connettersi a un cluster a nodo singolo Kubernetes in AKS con `kubectl`. 

   >[!NOTE]
   >Per evitare l'errore del nodo, un cluster Kubernetes richiede più di un nodo.

* **2.0.23 CLI di Azure**
   - Le istruzioni riportate in questa esercitazione sono state convalidate rispetto 2.0.23 CLI di Azure.

## <a name="create-sa-password"></a>Password dell'account SA di creazione

Creare una password per SA nel cluster Kubernetes. Kubernetes può gestire le informazioni di configurazione sensibili come le password come [segreti](http://kubernetes.io/docs/concepts/configuration/secret/).

Il comando seguente crea una password per l'account SA:

   ```azurecli
   kubectl create secret generic mssql --from-literal=SA_PASSWORD="MyC0m9l&xP@ssw0rd"
   ```  

   Sostituire `MyC0m9l&xP@ssw0rd` con una password complessa.

   Per creare una chiave privata in Kubernetes denominato `mssql` che contiene il valore `MyC0m9l&xP@ssw0rd` per il `SA_PASSWORD`, eseguire il comando.


## <a name="create-storage"></a>Creare spazio di archiviazione

Configurare un [volume permanente](http://kubernetes.io/docs/concepts/storage/persistent-volumes/), e [volume permanente attestazione](http://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistent-volume-claim-protection) nel cluster Kubernetes. Completare i passaggi seguenti: 

1. Creare un manifesto per definire la classe di archiviazione e il volume permanente attestazione.  Il manifesto specifica il provisioning di archiviazione, parametri e [recuperare criteri](http://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaiming). Il cluster Kubernetes utilizza il manifesto per creare l'archivio permanente. 

   Nell'esempio seguente viene yaml definisce una classe di archiviazione e l'attestazione volume permanente. Il provisioning di classe di archiviazione è `azure-disk` perché questo cluster Kubernetes in Azure. Il tipo di account di archiviazione è `Standard_LRS`. L'attestazione volume permanente è denominato `mssql-data`. I metadati di attestazione volume permanente includono un'annotazione connettersi nuovamente alla classe di archiviazione. 

   ```yaml
   kind: StorageClass
   apiVersion: storage.k8s.io/v1beta1
   metadata:
        name: azure-disk
   provisioner: kubernetes.io/azure-disk
   parameters:
     storageaccounttype: Standard_LRS
     kind: Managed
   ---
   kind: PersistentVolumeClaim
   apiVersion: v1
   metadata:
     name: mssql-data
     annotations:
       volume.beta.kubernetes.io/storage-class: azure-disk
   spec:
     accessModes:
     - ReadWriteOnce
     resources:
       requests:
         storage: 8Gi
   ```

   Salvare il file, ad esempio **pvc.yaml**.

1. Creare l'attestazione volume persistente in Kubernetes.

   ```azurecli
   kubectl apply -f <Path to pvc.yaml file>
   ```

   * `<Path to pvc.yaml file>`
      * Il percorso in cui è stato salvato il file.

   Il volume permanente è automaticamente creato come un account di archiviazione di Azure e associato al attestazione volume permanente. 

    ![Comando attestazione volume permanente](media/tutorial-sql-server-containers-kubernetes/02_pvc_cmd.png)

1. Verificare l'attestazione volume permanente.

   ```azurecli
   kubectl describe pvc <PersistentVolumeClaim>
   ```

   * `<PersistentVolumeClaim>`
      * Il nome dell'attestazione volume permanente.

    Nel passaggio precedente, l'attestazione permanente volume denominato `mssql-data`. Per visualizzare i metadati sull'attestazione permanente volume, eseguire il comando seguente:

    ```azurecli
    kubectl describe pvc mssql-data
    ```

    I metadati restituiti includono un valore denominato `Volume`. Questo valore è associato al nome del blob.

    ![Descrivere volume](media/tutorial-sql-server-containers-kubernetes/describe-volume.png)

    Il valore per il volume, parte di corrispondenze del nome del blob nell'immagine seguente dal portale di Azure: 

    ![Vengono descritti il portale di volume](media/tutorial-sql-server-containers-kubernetes/describe-volume-portal.png)

1. Verificare il volume permanente.

   ```azurecli
   kubectl describe pv
   ```

   `kubectl`Restituisce i metadati sul volume persistente che è stato automaticamente creato e associato al volume permanente attestazione. 

## <a name="create-the-deployment"></a>Creare la distribuzione

In questo esempio, il contenitore che ospita l'istanza di SQL Server viene descritto come un oggetto di distribuzione Kubernetes. La distribuzione crea un set di repliche. Il set di repliche crea il pod. 

In questo passaggio, creare un manifesto per descrivere il contenitore in base a Microsoft SQL Server [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) immagine Docker. I riferimenti del manifesto di `mssql-server` attestazione volume permanente e `mssql` segreto che è già stato applicato al cluster Kubernetes. Il manifesto descrive anche un [servizio](http://kubernetes.io/docs/concepts/services-networking/service/). Questo servizio è un servizio di bilanciamento del carico. Il bilanciamento del carico garantisce che l'indirizzo IP viene mantenuta dopo avere recuperata l'istanza di SQL Server. 

1. Creare un manifesto - yaml - per descrivere la distribuzione. L'esempio seguente illustra una distribuzione incluso un contenitore in base all'immagine di contenitore di SQL Server.

   ```yaml
   apiVersion: apps/v1beta1
   kind: Deployment
   metadata:
     name: mssql-deployment
   spec:
     replicas: 1
     template:
       metadata:
         labels:
           app: mssql
       spec:
         terminationGracePeriodSeconds: 10
         containers:
         - name: mssql
           image: microsoft/mssql-server-linux
           ports:
           - containerPort: 1433
           env:
           - name: ACCEPT_EULA
             value: "Y"
           - name: SA_PASSWORD
             valueFrom:
               secretKeyRef:
                 name: mssql
                 key: SA_PASSWORD 
           volumeMounts:
           - name: mssqldb
             mountPath: /var/opt/mssql
         volumes:
         - name: mssqldb
           persistentVolumeClaim:
             claimName: mssql-data
   ---
   apiVersion: v1
   kind: Service
   metadata:
     name: mssql-deployment
   spec:
     selector:
       app: mssql
     ports:
       - protocol: TCP
         port: 1433
         targetPort: 1433
     type: LoadBalancer
   ```

   Copiare il codice precedente in un nuovo file denominato `sqldeployment.yaml`. Aggiornare i valori seguenti: 

   * `value: "Developer"`
     * Imposta il contenitore per l'esecuzione di SQL Server Developer edition. Edizione Developer non è concesso in licenza per i dati di produzione. Se la distribuzione di produzione, impostare l'edizione appropriata. Può essere uno dei `Enterprise`, `Standard`, o `Express`. 

      >[!NOTE]
      >Per ulteriori informazioni, vedere [come licenza SQL Server](http://www.microsoft.com/sql-server/sql-server-2017-pricing).

   * `persistentVolumeClaim`
     * È necessario che una voce per `claimName:` che esegue il mapping al nome utilizzato per l'attestazione volume permanente. Questo articolo usa `mssql-data`. 

   * `name: SA_PASSWORD`
      * Consente di configurare l'immagine di contenitore per impostare la password SA come definito in questa sezione.

      ```yaml
      valueFrom:
        secretKeyRef:
          name: mssql
          key: SA_PASSWORD 
      ```

       Quando Kubernetes consente di distribuire il contenitore, fa riferimento al segreto denominato `mssql` per ottenere il valore per la password. 

   >[!NOTE]
   >Tramite il `LoadBalancer` tipo di servizio, l'istanza di SQL Server è accessibile in remoto (tramite internet) alla porta 1433.

    Salvare il file, ad esempio **sqldeployment.yaml**.

1. Creare la distribuzione.

   ```azurecli
   kubectl apply -f <Path to sqldeployment.yaml file>
   ```

   * `<Path to sqldeployment.yaml file>`
      * Il percorso in cui è stato salvato il file.

   ![Comando di distribuzione](media/tutorial-sql-server-containers-kubernetes/04_deploy_cmd.png)

   La distribuzione e il servizio vengono creati. L'istanza di SQL Server è in un contenitore - connesso a un archivio permanente.

   Per visualizzare lo stato di pod, digitare `kubectl get pod`.

   ![Comando pod Get](media/tutorial-sql-server-containers-kubernetes/05_get_pod_cmd.png)

   >[!NOTE]
   >Dopo aver creata la distribuzione, potrebbe richiedere alcuni minuti prima di pod è visibile. Il ritardo è perché il cluster deve effettuare il pull di [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) immagine dall'hub Docker. Dopo la prima volta viene effettuato il pull, nelle distribuzioni successive possono essere più veloci - se la distribuzione a un nodo che dispone già di immagine memorizzati nella cache su di esso. 

1. Verificare che i servizi siano in esecuzione. Eseguire il comando seguente:

   ```azurecli
   kubectl get services 
   ```

   Questo comando restituisce i servizi in esecuzione, nonché gli indirizzi IP interni ed esterni per i servizi. Prendere nota dell'indirizzo IP esterno per il `mssql-deployment` servizio.  Utilizzare questo indirizzo IP per connettersi a SQL Server. 

   ![Ottenere il comando di servizio](media/tutorial-sql-server-containers-kubernetes/06_get_service_cmd.png)

   Per ulteriori informazioni sullo stato degli oggetti nel cluster Kubernetes, eseguire:

   ```azurecli
   az aks browse --resource-group <MyResourceGroup> --name <MyKubernetesClustername>
   ```  

## <a name="connect-to-the-sql-server-instance"></a>Connettersi all'istanza di SQL Server

Se il contenitore è stato configurato come descritto, è possibile connettersi a un'applicazione all'esterno della rete virtuale di Azure. Utilizzare il `sa` account e l'indirizzo IP esterno di indirizzi per il servizio. Utilizzare la password configurati come segreto Kubernetes. 

Per connettersi all'istanza di SQL Server, è possibile utilizzare le seguenti applicazioni. 

* [SQL SERVER MANAGEMENT STUDIO](http://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-ssms)

* [SSDT](http://docs.microsoft.com/en-us/sql/linux/sql-server-linux-develop-use-ssdt)

* SQLCMD per la connessione con `sqlcmd`, eseguire il comando seguente:

   ```cmd
   sqlcmd -S <External IP Address> -U sa -P "MyC0m9l&xP@ssw0rd"
   ```

   Sostituire i valori seguenti:
      - `<External IP Address>`con l'indirizzo IP per il `mssql-deployment` servizio 
      - `MyC0m9l&xP@ssw0rd`con la password

## <a name="verify-failure-and-recovery"></a>Verificare l'errore e ripristino

Per verificare l'errore e il ripristino è possibile eliminare il pod. Effettuare i passaggi seguenti:

1. Elenco di pod che esegue SQL Server.

   ```azurecli
   kubectl get pods
   ```

   Annotare il nome del pod che esegue SQL Server.

1. Eliminare il pod.

   ```azurecli
   kubectl delete pod mssql-deployment-0
   ```
   `mssql-deployment-0`il valore viene restituito nel passaggio precedente per nome pod. 

Kubernetes ricrea automaticamente il pod per ripristinare un'istanza di SQL Server e connettersi all'archivio permanente. Utilizzare `kubectl get pods` per verificare che venga distribuito un nuovo pod. Utilizzare `kubectl get services` per verificare che l'indirizzo IP per il nuovo contenitore sia lo stesso. 

## <a name="summary"></a>Riepilogo

In questa esercitazione è stato descritto come distribuire i contenitori di SQL Server a un cluster Kubernetes per la disponibilità elevata. 

> [!div class="checklist"]
> * Password dell'account SA di creazione
> * Creare spazio di archiviazione
> * Creare una distribuzione
> * La connessione con SQL Server Management Studio (SSMS)
> * Verificare l'errore e ripristino

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
>[Introduzione - Kubernetes](http://docs.microsoft.com/en-us/azure/aks/intro-kubernetes)
