---
title: Che cos'è un pool di calcolo cluster SQL dei big Data? | Microsoft Docs
description: Questo articolo descrive il pool di calcolo in un cluster di big data di SQL Server 2019.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 6aa73c5881a4b6a17e190c26c15f97b3d8c79c14
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221797"
---
# <a name="what-is-a-sql-big-data-clusters-compute-pool"></a>Che cos'è un pool di calcolo cluster SQL dei big Data?

Questo articolo descrive il ruolo del *pool di calcolo di SQL Server* in un cluster di big data anteprima di SQL Server 2019. I pool di calcolo offrono le risorse di calcolo a scalabilità orizzontale per un cluster di big data. Le sezioni seguenti descrivono l'architettura e la funzionalità di un pool di calcolo.

## <a name="compute-pool-architecture"></a>Architettura del pool di calcolo

Un pool di calcolo è costituito da uno o più POD in esecuzione in Kubernetes di calcolo. La creazione automatica e la gestione di questi POD è coordinata dal [istanza master di SQL Server](concept-master-instance.md). Ogni pod contiene un set di servizi di base e un'istanza del motore di database di SQL Server.

> [!NOTE]
> CTP 2.1 supporta solo un pool di calcolo singolo per ogni cluster.

## <a name="scale-out-groups"></a>Gruppi con scalabilità orizzontale

Un pool di calcolo può fungere da un gruppo con scalabilità orizzontale PolyBase per le query distribuite su origini dati differenti, ad esempio HDFS, Oracle, MongoDB o Terradata. Usando i POD di calcolo in Kubernetes, è possono automatizzare i cluster di big data creazione e configurazione di calcolo POD per gruppi con scalabilità orizzontale di PolyBase.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui cluster di big data di SQL Server, vedere Panoramica riportata di seguito:

- [Quali sono i cluster di SQL Server 2019 dei big Data?](big-data-cluster-overview.md)
