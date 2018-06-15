---
title: Backup e il caricamento di hardware - Parallel Data Warehouse
description: Per distribuire i end-to-end soluzione di data warehousing su Analitica piattaforma di strumenti con Parallel Data Warehouse (PDW), è necessario creare un piano di backup del data warehouse e il caricamento dei dati. Utilizzare questa guida per acquisire e configurare i server di backup e il caricamento in grado di soddisfare i requisiti aziendali.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4d7f7b6b4edea9dacab7287a7936b7fd87fd7973
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31544733"
---
# <a name="backup-and-loading-hardware-overview---parallel-data-warehouse"></a>Backup e il caricamento Cenni preliminari sull'hardware - Parallel Data Warehouse
Per distribuire i end-to-end soluzione di data warehousing su Analitica piattaforma di strumenti con Parallel Data Warehouse (PDW), è necessario creare un piano di backup del data warehouse e il caricamento dei dati. Utilizzare questa guida per acquisire e configurare i server di backup e il caricamento in grado di soddisfare i requisiti aziendali.  
  
## <a name="acquire-and-configure-backup-servers"></a>Acquisire e configurare i server di backup  
![Processo di backup](media/backup-process.png "processo di Backup")  
  
Per eseguire il backup di un database PDW, è necessario uno o più server di backup. È possibile utilizzare l'hardware esistente o acquistare nuovo hardware. Per ulteriori informazioni, vedere [acquisire e configurare un Server di Backup](acquire-and-configure-backup-server.md). Queste istruzioni includono un [Backup foglio di lavoro di pianificazione della capacità server](backup-capacity-planning-worksheet.md) per facilitare la pianificazione della soluzione ideale per backup.  
  
## <a name="acquire-and-configure-loading-servers"></a>Acquisire e configurare il caricamento dei server  
![Processo di caricamento](media/loading-process.png "processo di caricamento")  
  
Per caricare i dati, è necessario uno o più server di caricamento. È possibile utilizzare la propria ETL esistenti o ad altri server o è possibile acquistare nuovi server. Per ulteriori informazioni, vedere [acquisizione e configurare un server di caricamento](acquire-and-configure-loading-server.md). Queste istruzioni includono un [durante il caricamento di foglio di lavoro di pianificazione della capacità server](loading-server-capacity-planning-worksheet.md) per pianificare la soluzione ideale per il caricamento.  
  
## <a name="see-also"></a>Vedere anche  
[Panoramica di backup e ripristino](backup-and-restore-overview.md)  
[Panoramica di carico](load-overview.md)  
  
