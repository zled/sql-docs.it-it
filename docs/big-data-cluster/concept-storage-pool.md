---
title: Che cos'è il pool di archiviazione cluster di SQL Server i big Data? | Microsoft Docs
description: Questo articolo descrive il pool di archiviazione in un cluster di big data di SQL Server 2019.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: cbf9ff14ece1b33e1c271786bc96f0ac590b807e
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050753"
---
# <a name="what-is-the-sql-server-big-data-clusters-storage-pool"></a>Che cos'è il pool di archiviazione cluster di SQL Server i big Data?

Questo articolo descrive il ruolo del *pool di archiviazione di SQL Server* in un cluster di big data anteprima di SQL Server 2019. Le sezioni seguenti descrivono l'architettura e la funzionalità di un pool di archiviazione SQL.

## <a name="storage-pool-architecture"></a>Architettura del pool di archiviazione

Il pool di archiviazione è costituito da archiviazione di nodi è costituiti da SQL Server in Linux, Spark e HDFS. Tutti i nodi di archiviazione in un cluster di big data SQL sono membri di un cluster HDFS.

![Architettura del pool di archiviazione](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Responsabilità

I nodi di archiviazione sono responsabili per:

- Inserimento dei dati tramite Spark.
- Archiviazione dei dati in HDFS (formato Parquet). HDFS offre anche la persistenza dei dati, come i dati HDFS sono distribuiti in tutti i nodi di archiviazione del cluster di big data SQL.
- Accesso ai dati tramite gli endpoint HDFS e SQL Server.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui cluster di big data di SQL Server, vedere Panoramica riportata di seguito:

- [Quali sono i cluster di SQL Server 2019 dei big Data?](big-data-cluster-overview.md)
