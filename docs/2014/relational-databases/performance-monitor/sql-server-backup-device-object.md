---
title: Oggetto Backup Device di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 62ba36e83f08cabda85fd71a02d4e22842fb0e8f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158890"
---
# <a name="sql-server-backup-device-object"></a>Oggetto Backup Device di SQL Server
  L'oggetto **Backup Device** include contatori per il monitoraggio dei dispositivi di backup di Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usati per le operazioni di backup e ripristino. Monitorare i dispositivi di backup se si desidera determinare la velocità effettiva oppure lo stato di avanzamento e le prestazioni delle operazioni di backup e ripristino per ogni dispositivo. Per monitorare la velocità effettiva di un'operazione di backup o ripristino dell'intero database, usare il contatore **Velocità effettiva backup o ripristino/sec** dell'oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** object. Per altre informazioni, vedere [SQL Server, Databases Object](sql-server-databases-object.md).  
  
 In questa tabella viene descritto il contatore dell'oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** counter.  
  
|Contatore dell'oggetto Backup Device di SQL Server|Description|  
|---------------------------------------|-----------------|  
|**Byte/sec velocità effettiva dispositivo**|Velocità effettiva delle operazioni di lettura e scrittura (in byte al secondo) di un dispositivo di backup utilizzato durante il backup o il ripristino dei database. Il contatore è disponibile solo durante l'esecuzione dell'operazione di backup o ripristino.|  
  
## <a name="see-also"></a>Vedere anche  
 [Dispositivi di backup &#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md)   
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](monitor-resource-usage-system-monitor.md)  
  
  