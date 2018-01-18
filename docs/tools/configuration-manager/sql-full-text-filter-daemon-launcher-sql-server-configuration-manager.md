---
title: Avvio del Daemon filtri Full-text SQL (Gestione configurazione SQL Server) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
caps.latest.revision: "8"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 324fc9e1d780d885aa90b2147ef563742dedcb43
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a>Utilità di avvio del daemon filtri full-text di SQL (Gestione configurazione SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], il servizio di avvio del Daemon di filtri Full-text di SQL (FDHOST Launcher) viene utilizzato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ricerca full-text per avviare il processo host del daemon filtri che gestisce il word breaking e filtro di ricerca full-text. Per utilizzare la ricerca full-text, questo servizio deve essere in esecuzione. Il servizio utilità di avvio di FDHOST è un servizio specifico dell'istanza associato a una determinata istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tale servizio propaga le informazioni sull'account del servizio a ogni processo host del daemon di filtri avviato. Per informazioni sui processi host del daemon di filtri, vedere "Architettura della ricerca full-text" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
  
