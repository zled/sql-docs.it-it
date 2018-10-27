---
title: Che cos'è un pool di dati i cluster SQL dei big Data? | Microsoft Docs
description: Questo articolo descrive il pool di dati in un cluster di big data di SQL Server 2019.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: bf47aa1734e2b1a849fb8333da9c914ea4244f41
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050764"
---
# <a name="what-is-a-sql-big-data-clusters-data-pool"></a>Che cos'è un pool di dati i cluster SQL dei big Data?

Questo articolo descrive il ruolo del *pool di dati di SQL Server* in un cluster di big data anteprima di SQL Server 2019. Le sezioni seguenti descrivono l'architettura e la funzionalità di un pool di dati SQL.

## <a name="data-pool-architecture"></a>Architettura di pool di dati

Un pool di dati è costituito da uno o più istanze del pool di dati SQL Server. Istanze del pool di dati SQL forniscono un archivio permanente SQL Server per il cluster. Un pool di dati viene utilizzato per inserire i dati dalla query SQL o i processi Spark. Per garantire prestazioni migliori in grandi set di dati, i dati in un pool di dati viene distribuiti in partizioni tra le istanze del pool di dati SQL membro.

## <a name="scale-out-data-marts"></a>Scalabilità orizzontale data mart

I pool di dati consentono la creazione di tipo scale-out data mart, in cui i dati esterni da più origini vengono inseriti in pool di dati. Poiché i dati viene distribuiti in istanze del pool di dati, le query parallele sui dati curati sono più efficienti.

![Data mart di dati di tipo scale-out](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui cluster di big data di SQL Server, vedere Panoramica riportata di seguito:

- [Quali sono i cluster di SQL Server 2019 dei big Data?](big-data-cluster-overview.md)
