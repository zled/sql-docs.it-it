---
title: Che cos'è un pool di calcolo cluster SQL dei big Data? | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: c17f6ac604edc021299f473137dcf6c5e470e3d4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796655"
---
# <a name="what-is-a-sql-big-data-clusters-compute-pool"></a>Che cos'è un pool di calcolo cluster SQL dei big Data?

Questo articolo descrive il ruolo del *pool di calcolo di SQL Server* preview 2019 un Server SQL cluster di Big Data. I pool di calcolo offrono le risorse di calcolo a scalabilità orizzontale per un cluster di Big Data. Le sezioni seguenti descrivono l'architettura e la funzionalità di un pool di calcolo.

## <a name="compute-pool-architecture"></a>Architettura del pool di calcolo

Un pool di calcolo è costituito da uno o più POD in esecuzione in Kubernetes di calcolo. La creazione automatica e la gestione di questi POD è coordinata dal [istanza master di SQL Server](concept-master-instance.md). Ogni pod contiene un set di servizi di base e un'istanza del motore di database di SQL Server.

> [!NOTE]
> Versioni da CTP 2.0 supporta solo un pool di calcolo singolo per ogni cluster.

## <a name="scale-out-groups"></a>Gruppi con scalabilità orizzontale

Un pool di calcolo può fungere da un gruppo con scalabilità orizzontale PolyBase per le query distribuite su origini dati differenti, ad esempio HDFS, Oracle, MongoDB o Terradata. Usando i POD di calcolo in Kubernetes, è possono automatizzare i cluster di big data creazione e configurazione di calcolo POD per gruppi con scalabilità orizzontale di PolyBase.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui cluster di big data di SQL Server, vedere Panoramica riportata di seguito:

- [Che cos'è SQL Server 2019 i cluster di big data?](big-data-cluster-overview.md)
