---
title: Opzioni per gli snapshot | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snapshot replication [SQL Server], options
- snapshots [SQL Server replication], options
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
caps.latest.revision: 27
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 62f5f6550cc6696cab12ca838dcd34669ee18a0a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169627"
---
# <a name="snapshot-options"></a>Opzioni per gli snapshot
  Quando si inizializza una sottoscrizione con uno snapshot è possibile:  
  
-   Specificare una posizione alternativa per la cartella snapshot in aggiunta a quella predefinita o al posto di questa. Per altre informazioni, vedere [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md).  
  
-   Comprimere gli snapshot per l'archiviazione sui supporti rimovibili o il trasferimento su una rete lenta. Per altre informazioni, vedere [Compressed Snapshots](compressed-snapshots.md).  
  
-   Eseguire gli script [!INCLUDE[tsql](../../includes/tsql-md.md)] prima o dopo aver applicato lo snapshot. Per altre informazioni, vedere [Eseguire gli script prima e dopo l'applicazione dello snapshot](execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Trasferire i file di snapshot mediante il protocollo FTP (File Transfer Protocol). Per altre informazioni, vedere [Trasferire snapshot tramite FTP](transfer-snapshots-through-ftp.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Inizializzazione di una sottoscrizione con uno snapshot](initialize-a-subscription-with-a-snapshot.md)  
  
  