---
title: Configurare il cluster di dischi condivisi per SQL Server in Linux | Documenti Microsoft
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 92b4cb2500d4fd8a1643488593c40e97b1ff6454
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---

# <a name="shared-disk-cluster-for-sql-server-on-linux"></a>Cluster di dischi condivisi per SQL Server in Linux

È possibile configurare un cluster a disponibilità elevata di memoria condivisa con Linux per consentire l'istanza di SQL Server per eseguire il failover da un nodo a un altro. In un cluster tipico due o più server sono connessi all'archiviazione condivisa. I server sono i nodi del cluster. Cluster di failover forniscono protezione a livello di istanza per ridurre i tempi di ripristino da per consentire a SQL Server per eseguire il failover tra due o più nodi. Passaggi di configurazione dipendono la distribuzione di Linux e soluzioni di clustering. Nella tabella seguente identifica i passaggi specifici per le soluzioni cluster convalidato.  

|Distribuzione |Argomento 
|----- |-----
|**Red Hat Enterprise Linux con il componente aggiuntivo a disponibilità elevata** |[Configurare](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Funzionamento](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server con il componente aggiuntivo a disponibilità elevata** |[Configurare](sql-server-linux-shared-disk-cluster-sles-configure.md)

## <a name="next-steps"></a>Passaggi successivi


