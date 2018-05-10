---
title: Aprire, visualizzare e stampare un file deadlock (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: performance
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 971e5ae6448c26cea0c7212fac45bad5ff26e08f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="open-view-and-print-a-deadlock-file-sql-server-management-studio"></a>Aprire, visualizzare e stampare un file deadlock (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Quando tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] viene generato un deadlock, è possibile acquisire e salvare le informazioni del deadlock in un file. Dopo avere salvato il file deadlock, è possibile aprirlo in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per visualizzarlo o stamparlo.  
  
## <a name="open-and-view-a-deadlock-file"></a>Aprire e visualizzare un file deadlock  
  
1. Scegliere **Apri** dal menu [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]File **di** e quindi selezionare **File**.  
  
2. Nella finestra di dialogo **Apri file** selezionare il tipo di file con estensione xdl nella casella **Tipo file** . Si ottiene un elenco filtrato contenente solo i file deadlock.  
  
## <a name="print-a-deadlock-file"></a>Stampare un file deadlock  
  
1. Scegliere **Apri** dal menu [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]File **di** e quindi selezionare **File**.  
  
2. Nella finestra di dialogo **Apri file** selezionare il tipo di file con estensione xdl nella casella **Tipo file** . Si ottiene un elenco filtrato contenente solo i file deadlock.  
  
3. Selezionare il file deadlock che si vuole stampare e quindi scegliere **Apri**.  
  
4. Scegliere **Stampa** dal menu **File**.  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare eventi Deadlock Graph &#40;SQL Server Profiler&#41;](../../relational-databases/performance/save-deadlock-graphs-sql-server-profiler.md)  
  
  
