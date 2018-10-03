---
title: Connettersi a SQL Server gruppo di disponibilità AlwaysOn nel cluster Kubernetes
description: Questo articolo illustra come connettersi a un gruppo di disponibilità AlwaysOn
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6092f15fe64c96ed004d352408ae6cdac034def9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852159"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>Connettersi a SQL Server Always On Availability Group nel Kubernetes

Per connettersi alle istanze di SQL Server in contenitori in un cluster Kubernetes, creare un [servizio di bilanciamento del carico](http://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer). Il servizio di bilanciamento del carico inoltra le richieste per l'indirizzo IP nel POD in esecuzione l'istanza di SQL Server.

Per connettersi a una replica del gruppo di disponibilità, creare un servizio per i tipi di replica diverse. È possibile visualizzare esempi di servizi per i diversi tipi di repliche [sql-server-samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml).

* `ag1-primary` punta alla replica primaria.
* `ag1-secondary-sync` punta alla replica secondaria sincrona.
* `ag1-secondary-async` punta a una replica secondaria asincrona.

Se non esiste più di una replica secondaria dello stesso tipo, Kubernetes indirizza la connessione per le diverse repliche secondo uno schema round-robin.

## <a name="create-a-load-balancer-service"></a>Creare un servizio di bilanciamento del carico

Per creare un servizio di bilanciamento del carico per la replica primaria, copiare `ag1-primary.yaml` dal [sql-server-samples]()e aggiornarlo per il gruppo di disponibilità.

Il comando seguente si applica il file con estensione yaml per il cluster:

```kubectl
kubectl apply -f ag1-primary.yaml
```

## <a name="get-the-ip-address-for-your-load-balancer-service"></a>Ottenere l'indirizzo IP per il servizio di bilanciamento del carico

Per ottenere l'indirizzo IP di bilanciamento del carico per il servizio di bilanciamento del carico, eseguire

```kubectl
kubectl get services
```

Identificare l'indirizzo IP del servizio che si desidera connettersi.

## <a name="connect-to-primary-replica"></a>Connettersi alla replica primaria

Per connettersi alla replica primaria con l'autenticazione di SQL, usare il `sa` account, il valore per `sapassword` dal segreto creato e questo indirizzo IP.

Esempio:

```cmd
sqlcmd -S <0.0.0.0> -U sa -P "<MyC0m9l&xP@ssw0rd>"
```

## <a name="next-steps"></a>Passaggi successivi

[Gestire il gruppo di disponibilità SQL Server in cluster Kubernetes](sql-server-linux-kubernetes-manage.md)

[Gruppo di disponibilità SQL Server in cluster Kubernetes](sql-server-ag-kubernetes.md)
