---
title: Backup e il caricamento Cenni preliminari sull'hardware per PDW APS
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "Per distribuire i end-to-end soluzione di data warehousing su Analitica piattaforma di strumenti analitici con SQL Server Parallel Data Warehouse (PDW), è necessario creare un piano di backup del data warehouse e il caricamento dei dati."
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 3a2ae046-f8d8-4a5c-b3c1-6ecee005df6c
caps.latest.revision: "9"
ms.openlocfilehash: 0bdf529aacf1644f55cd44da3d0a7590e509a323
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="backup-and-loading-hardware-overview"></a>Backup e il caricamento Cenni preliminari sull'hardware
Per distribuire i end-to-end soluzione di data warehousing su Analitica piattaforma di strumenti analitici con SQL Server Parallel Data Warehouse (PDW), è necessario creare un piano di backup del data warehouse e il caricamento dei dati. Utilizzare questa guida per acquisire e configurare i server di backup e il caricamento in grado di soddisfare i requisiti aziendali.  
  
## <a name="acquire-and-configure-backup-servers"></a>Acquisire e configurare i server di backup  
![Processo di backup](media/backup-process.png "processo di Backup")  
  
Per eseguire il backup di un database PDW, è necessario uno o più server di backup. È possibile utilizzare l'hardware esistente o acquistare nuovo hardware. Per ulteriori informazioni, vedere [acquisire e configurare un Server di Backup](acquire-and-configure-backup-server.md). Queste istruzioni includono un [Backup foglio di lavoro di pianificazione della capacità server](backup-capacity-planning-worksheet.md) per facilitare la pianificazione della soluzione ideale per backup.  
  
## <a name="acquire-and-configure-loading-servers"></a>Acquisire e configurare il caricamento dei server  
![Processo di caricamento](media/loading-process.png "processo di caricamento")  
  
Per caricare i dati, è necessario uno o più server di caricamento. È possibile utilizzare la propria ETL esistenti o ad altri server o è possibile acquistare nuovi server. Per ulteriori informazioni, vedere [acquisizione e configurare un server di caricamento](acquire-and-configure-loading-server.md). Queste istruzioni includono un [durante il caricamento di foglio di lavoro di pianificazione della capacità server](loading-server-capacity-planning-worksheet.md) per pianificare la soluzione ideale per il caricamento.  
  
## <a name="see-also"></a>Vedere anche  
[Panoramica di backup e ripristino](backup-and-restore-overview.md)  
[Panoramica di carico](load-overview.md)  
  
