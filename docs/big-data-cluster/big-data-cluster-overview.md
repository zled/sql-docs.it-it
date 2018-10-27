---
title: Quali sono i cluster di SQL Server 2019 dei big Data? | Microsoft Docs
description: Informazioni sui cluster di big data 2019 di SQL Server (anteprima) che vengono eseguiti su Kubernetes e fornire le opzioni di scalabilità orizzontale per relazionali e dati di HDFS.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/25/2018
ms.topic: overview
ms.prod: sql
ms.openlocfilehash: 7648988fb861531a403efe17b883f53eca8e5dbe
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50051003"
---
# <a name="what-are-sql-server-2019-big-data-clusters"></a>Quali sono i cluster di SQL Server 2019 dei big Data?

A partire da [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)], i cluster di big data di SQL Server consentono di distribuire cluster scalabili di contenitori Docker di HDFS, Spark e SQL Server in esecuzione in Kubernetes. Questi componenti sono in esecuzione side-by-side per consentire la lettura, scrittura ed elaborare big data da Transact-SQL o Spark. I cluster di big data di SQL Server consentono di combinare e analizzare i dati relazionali di valore elevato con volumi elevati di big data con facilità.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="scenarios"></a>Scenari

I cluster di SQL Server i big data offrono flessibilità nella modalità di interazione con i big data. È possibile eseguire query delle origini dati esterne, archivia i big data in HDFS gestiti da SQL Server o per estrarre i dati da più origini dati nel cluster. È quindi possibile usare i dati per intelligenza artificiale, Machine Learning e altre attività di analisi. Le sezioni seguenti forniscono altre informazioni su questi scenari.

### <a name="data-virtualization"></a>Virtualizzazione dei dati

Sfruttando [PolyBase di SQL Server](../relational-databases/polybase/polybase-guide.md), i cluster di big data di SQL Server possono eseguire una query su origini dati esterne l'importazione dei dati. [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] introduce nuovi connettori alle origini dati.

![Virtualizzazione dei dati](media/big-data-cluster-overview/data-virtualization.png)

### <a name="data-lake"></a>Lake dati

Un cluster di big data di SQL Server include un HDFS scalabile *pool di archiviazione*. Può essere utilizzato per archivia direttamente i big data, potenzialmente acquisiti da più origini esterne. Una volta nel cluster di big data, è possibile analizzare e query sui dati e combinarli con i dati relazionali di alto valore.

![Lake dati](media/big-data-cluster-overview/data-lake.png)

### <a name="scale-out-data-mart"></a>Data mart di dati di tipo scale-out

I cluster di big data di SQL Server forniscono scalabilità orizzontale calcolo e archiviazione per migliorare le prestazioni di analisi dei dati. I dati da diverse origini possono essere inseriti e distribuiti tra *pool di dati* nodi per un'ulteriore analisi.

![data mart di data](media/big-data-cluster-overview/data-mart.png)

### <a name="integrated-ai-and-machine-learning"></a>Machine Learning e intelligenza artificiale integrata

I cluster di big data di SQL Server consentono di attività sui dati archiviati nei dati del pool di archiviazione HDFS e i pool di dati di machine learning e intelligenza artificiale. È possibile usare Spark e gli strumenti di intelligenza artificiale incorporati in SQL Server tramite R, Python o Java.

![Machine Learning e intelligenza artificiale](media/big-data-cluster-overview/ai-ml-spark.png)

### <a name="management-and-monitoring"></a>Gestione e monitoraggio

Gestione e monitoraggio vengono forniti tramite una combinazione di componenti open source, strumenti di SQL Server e viste a gestione dinamica.

Il [del portale di amministrazione Cluster](cluster-admin-portal.md) è un'interfaccia web che consente di visualizzare lo stato e integrità dei POD nel cluster. Vengono inoltre forniti collegamenti ad altri dashboard fornito da Grafana e Kibana.

È possibile utilizzare Data Studio di Azure per eseguire una serie di attività nel cluster di big data. Questa opzione è abilitata per il nuovo **estensione 2019 per Server SQL (anteprima)**. Questa estensione offre:

- Frammenti predefiniti per attività comuni di gestione.
- Report sul numero di pool di calcolo e lo stato dei processi in esecuzione.
- Report sullo stato dei processi di Spark e HDFS.
- Possibilità di esplorare HDFS, caricare i file, i file di anteprima e creare una directory.
- Possibilità di creare, aprire ed eseguire i notebook di Jupyter compatibile.
- Data virtualization procedura guidata per semplificare la creazione di origini dati esterne.

## <a id="architecture"></a> Architettura

Un cluster di big data di SQL Server è un cluster di nodi di Linux orchestrata dal [Kubernetes](https://kubernetes.io/docs/concepts/).

### <a name="kubernetes-concepts"></a>Concetti relativi a Kubernetes

Kubernetes è un agente di orchestrazione di contenitori di open source, che è possibile ridimensionare le distribuzioni di contenitori in base alle esigenze. La tabella seguente vengono definiti alcuni termini importanti di Kubernetes:

|||
|--|--|
| **Cluster** | Un cluster Kubernetes è un set di computer, noti come nodi. Un nodo controlla il cluster e viene designato del nodo master; i nodi rimanenti sono nodi di lavoro. Il master di Kubernetes è responsabile per la distribuzione del lavoro tra i ruoli di lavoro e per il monitoraggio dell'integrità del cluster. |
| **Node** | Un nodo esegue le applicazioni nei contenitori. Può trattarsi di un computer fisico o una macchina virtuale. Un cluster Kubernetes può contenere una combinazione di nodi macchina virtuale e computer fisici. |
| **POD** | Un pod è l'unità atomica di Kubernetes. Un pod è un gruppo logico di uno o più contenitori e le risorse associate, necessari per eseguire un'applicazione. Ogni pod viene eseguito su un nodo. un nodo può essere eseguito una o più POD. Il master di Kubernetes assegna automaticamente i POD per i nodi del cluster. |

Nei cluster di SQL Server i big data, Kubernetes è responsabile per lo stato dei cluster di big data di SQL Server; Kubernetes compila e configura i nodi del cluster, assegna i POD a nodi e monitora l'integrità del cluster.

### <a name="big-data-clusters-architecture"></a>architettura per big data cluster

I nodi del cluster sono organizzati in tre piani logici: il piano di controllo, nel riquadro calcolo e il piano dati. Ogni piano ha responsabilità diverse nel cluster. Tutti i nodi Kubernetes in un cluster di big data di SQL Server sono membro di almeno un piano.

![Panoramica dell'architettura](media/big-data-cluster-overview/architecture-diagram-planes.png)

### <a id="controlplane"></a> Piano di controllo

Il piano di controllo offre gestione e sicurezza per il cluster. Contiene il master di Kubernetes, il *istanza master di SQL Server*e altri servizi a livello di cluster, ad esempio il Metastore Hive e il Driver Spark.

### <a id="computeplane"></a> Piano di calcolo

Il piano di calcolo offre le risorse di calcolo al cluster. Contiene i nodi in esecuzione SQL Server in Linux POD. I POD nel piano di calcolo sono suddivise *pool di calcolo* per specifiche attività di elaborazione. Un pool di calcolo può agire come un [PolyBase](../relational-databases/polybase/polybase-guide.md) gruppo di scalabilità orizzontale per le query distribuite su origini dati diverse, ovvero, ad esempio HDFS, Oracle, MongoDB o Teradata.

### <a id="dataplane"></a> Piano dati

Il piano dati viene usato per la persistenza dei dati e la memorizzazione nella cache. Contiene il pool di dati SQL e i nodi di archiviazione.  Il pool di dati SQL è costituito da uno o più nodi che eseguono SQL Server in Linux. Viene utilizzato per inserire i dati dalla query SQL o i processi Spark. Dati di SQL Server big data mart vengono rese persistenti nel pool di dati del cluster. Il pool di archiviazione è costituito da archiviazione di nodi è costituiti da SQL Server in Linux, Spark e HDFS. Tutti i nodi di archiviazione in un cluster di big data di SQL Server sono membri di un cluster HDFS.

## <a name="next-steps"></a>Passaggi successivi

I cluster di big data di SQL Server sia disponibile come anteprima pubblica limitata tramite il programma di adozione anticipata SQL Server 2019. Per richiedere l'accesso, registrare [qui](https://aka.ms/eapsignup)e specificare l'interesse dimostrato per provare i cluster di big data. Microsoft valuta tutte le richieste e risposta appena possibile.