---
title: Replica di SQL Server in Linux | Microsoft Docs
description: Questo articolo descrive la replica di SQL Server in Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/20/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a6c4bad8947944d59208a0516e5950d36f64a84e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47734129"
---
# <a name="sql-server-replication-on-linux"></a>Replica di SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] introduce la replica di SQL Server per le istanze di SQL Server in Linux.

Configurare la replica in Linux con SQL Server Management Studio (SSMS) [stored procedure di replica](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

Può far parte di un'istanza di SQL Server in qualsiasi ruolo replica:

* Server di pubblicazione
* Database di distribuzione
* Sottoscrittore

Uno schema di replica può combinarsi e corrispondere piattaforme del sistema operativo. Ad esempio, uno schema di replica può usare le istanze di SQL Server in Linux per la distribuzione e la pubblicazione e sottoscrittori possono includere istanze di SQL Server in Windows.

Istanze di SQL Server in Linux possono partecipare a un tipo di replica.

* Transazionale
* Merge
* Snapshot

Per informazioni dettagliate sulla replica, vedere [documentazione di SQL Server replica](../relational-databases/replication/sql-server-replication.md).

## <a name="supported-features"></a>Caratteristiche supportate

Per [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] sono supportate le funzionalità di replica seguenti:

* Replica snapshot
* Replica transazionale
* Replica di tipo merge
* Replica peer-to-Peer
* Replica con porte non predefinite <!--Add link to explanation-->
* Replica con l'autenticazione di AD
* Configurazioni di replica in Windows e Linux
* Aggiornamenti immediati per la replica transazionale

## <a name="limitations"></a>Limitazioni

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] non supporta le funzionalità seguenti:

* Sottoscrittori di aggiornamento immediato

## <a name="next-steps"></a>Passaggi successivi

[Configurare la replica di SQL Server in Linux](sql-server-linux-replication-tutorial-tsql.md)

[Esempio: Configurare la replica di SQL Server in Linux](sql-server-linux-replication-configure.md)
