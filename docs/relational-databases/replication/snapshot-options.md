---
title: Opzioni per gli snapshot | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], options
- snapshots [SQL Server replication], options
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
caps.latest.revision: 28
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8781d62876e0ba8cd916ddcde1cf53f952c6bdf3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32961229"
---
# <a name="snapshot-options"></a>Opzioni per gli snapshot
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Quando si inizializza una sottoscrizione con uno snapshot è possibile:  
  
-   Specificare una posizione alternativa per la cartella snapshot in aggiunta a quella predefinita o al posto di questa. Per altre informazioni, vedere [Alternate Snapshot Folder Locations](../../relational-databases/replication/alternate-snapshot-folder-locations.md).  
  
-   Comprimere gli snapshot per l'archiviazione sui supporti rimovibili o il trasferimento su una rete lenta. Per altre informazioni, vedere [Compressed Snapshots](../../relational-databases/replication/compressed-snapshots.md).  
  
-   Eseguire gli script [!INCLUDE[tsql](../../includes/tsql-md.md)] prima o dopo aver applicato lo snapshot. Per altre informazioni, vedere [Eseguire gli script prima e dopo l'applicazione dello snapshot](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Trasferire i file di snapshot mediante il protocollo FTP (File Transfer Protocol). Per altre informazioni, vedere [Trasferire snapshot tramite FTP](../../relational-databases/replication/transfer-snapshots-through-ftp.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
