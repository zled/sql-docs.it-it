---
title: Che cos'è il controller del cluster di SQL Server i big Data? | Microsoft Docs
description: ''
author: mihaelablendea
ms.author: mihaelab
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: cb6a999c1ca791eea683e71e37ac788b8018672e
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460606"
---
# <a name="what-is-the-sql-server-big-data-clusters-controller"></a>Che cos'è il controller di cluster di SQL Server i big Data?

Il controller ospita la logica di base per distribuire e gestire un cluster di big data. Si occupa di tutte le interazioni con Kubernetes, le istanze di SQL Server che fanno parte del cluster e altri componenti come HDFS e Spark. 

Il servizio controller fornisce le funzionalità di base seguenti:

- Gestione del ciclo di vita del cluster: bootstrap del cluster & eliminazione, aggiornare le configurazioni
- Gestire le istanze di SQL Server master
- Gestire i pool di calcolo, dati e archiviazione
- Esporre gli strumenti di monitoraggio per osservare lo stato del cluster
- Esporre gli strumenti di risoluzione dei problemi per rilevare e correggere problemi imprevisti
- Gestire la sicurezza del cluster: verificare che gli endpoint cluster protetto, gestire utenti e ruoli, configurare le credenziali per la comunicazione all'interno del cluster
- Gestire il flusso di lavoro degli aggiornamenti in modo che vengono implementate in modo sicuro (non disponibile nella versione CTP 2.0)
- Gestire la disponibilità elevata e ripristino di emergenza per i servizi con stato nel cluster (non disponibile nella versione CTP 2.0)

## <a name="deploying-the-controller-service"></a>Distribuzione del servizio controller

Il controller è distribuito e ospitato nello spazio dei nomi Kubernetes stesso in cui il cliente vuole compilare un cluster di big data. Questo servizio viene installato da un amministratore di Kubernetes durante il bootstrap del cluster, tramite l'utilità della riga di comando mssqlctl:

```bash
mssqlctl create cluster <name of your cluster>
```

Il flusso di lavoro di costruzione verrà layout su Kubernetes un cluster di big data completamente funzionale di SQL Server che include tutti i componenti descritti nel [Panoramica](big-data-cluster-overview.md) articolo. Il flusso di lavoro bootstrap crea innanzitutto il servizio controller, e ciò è sufficiente distribuire il servizio controller si coordina l'installazione e configurazione del resto della parte i servizi del master, calcolo, dati e pool di archiviazione.

## <a name="managing-the-cluster-through-the-controller-service"></a>La gestione del cluster tramite il servizio controller
È possibile gestire il cluster esclusivamente tramite il servizio di controller usando `mssqlctl` API o il portale di amministrazione cluster ospitato all'interno del cluster. Se si distribuiscono oggetti aggiuntivi di Kubernetes, ad esempio i POD nello spazio dei nomi stesso, non sono gestiti o monitorati dal servizio controller.

Il controller e gli oggetti Kubernetes (set di informazioni sullo stato, i POD, segreti e così via) creati per un cluster di big data si trovano in uno spazio dei nomi Kubernetes dedicato. Il servizio controller verrà concesse le autorizzazioni dall'amministratore del cluster Kubernetes per gestire tutte le risorse all'interno di tale spazio dei nomi.  I criteri RBAC per questo scenario viene configurato automaticamente come parte della distribuzione iniziale del cluster usando `mssqlctl`. 

### <a name="mssqlctl"></a>mssqlctl

`mssqlctl` è un'utilità della riga di comando scritta in Python che consente agli amministratori di cluster da avviare e gestire i cluster di big data tramite le API REST esposta dal servizio controller.

### <a name="cluster-administration-portal"></a>Portale di amministrazione del cluster

Quando il servizio controller è attivo e in esecuzione, amministratore del cluster è possibile usare il portale di amministrazione Cluster per monitorare l'avanzamento della distribuzione, rilevare e risolvere i problemi con i servizi all'interno del cluster. 

## <a name="monitoring-and-troubleshooting-the-controller-service"></a>Monitoraggio e risoluzione dei problemi del servizio controller

Prossimamente...

## <a name="controller-service-security"></a>Sicurezza del servizio controller
Tutte le comunicazioni per il servizio controller viene effettuata tramite l'API REST su HTTPS. Un certificato autofirmato verrà automaticamente generato automaticamente in fase di bootstrap. 

L'autenticazione all'endpoint del servizio controller è basato su nome utente e password. Vengono effettuato il provisioning di queste credenziali in fase di bootstrap del cluster usando l'input per le variabili di ambiente `CONTROLLER_USERNAME` e `CONTROLLER_PASSWORD`.
```

> [!NOTE]
> You must provide a password that is in compliance with [SQL Server password complexity requirements](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017).

## Next steps

To learn more about the SQL Server big data clusters, see the following overview:

- [What is SQL Server 2019 big data clusters?](big-data-cluster-overview.md)
