---
title: Configurare il cluster di dischi condivisi per SQL Server in Linux | Documenti Microsoft
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/23/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: b6e6cc415b01c6021a4ba7c52433543dc58a4452
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="shared-disk-cluster-for-sql-server-on-linux"></a>Cluster di dischi condivisi per SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

È possibile configurare un cluster a disponibilità elevata di memoria condivisa con Linux per consentire l'istanza di SQL Server per eseguire il failover da un nodo a un altro. In un cluster tipico due o più server sono connessi all'archiviazione condivisa. I server sono i nodi del cluster. Cluster di failover forniscono protezione a livello di istanza per ridurre i tempi di ripristino da per consentire a SQL Server per eseguire il failover tra due o più nodi. Passaggi di configurazione dipendono la distribuzione di Linux e soluzioni di clustering. Nella tabella seguente identifica i passaggi specifici per le soluzioni cluster convalidato.  

|Distribuzione |Argomento 
|----- |-----
|**Red Hat Enterprise Linux con il componente aggiuntivo a disponibilità elevata** |[Configurare](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Funzionamento](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server con il componente aggiuntivo a disponibilità elevata** |[Configurare](sql-server-linux-shared-disk-cluster-sles-configure.md)

