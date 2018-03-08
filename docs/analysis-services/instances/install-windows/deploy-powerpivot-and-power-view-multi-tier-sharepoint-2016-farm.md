---
title: "Distribuire PowerPivot e Power View - Farm di SharePoint 2016 a più livelli | Documenti Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e36a632-0750-4247-92b6-1fe38c7a4ce2
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: da59f6eddb113c8af70e3ddcf3bcb3f35d6a6123
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="deploy-powerpivot-and-power-view---multi-tier-sharepoint-2016-farm"></a>Distribuire PowerPivot e Power View - Farm di SharePoint 2016 a più livelli
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  **Riepilogo:** Riepilogo: questo white paper offre agli architetti e agli amministratori di SharePoint istruzioni dettagliate per la distribuzione e la configurazione di un ambiente demo di Microsoft Business Intelligence in una farm di SharePoint con più server, sulla base delle versioni di anteprima di SharePoint Server 2016, di Office Online Server e dello stack di Business Intelligence di SQL Server 2016 per SharePoint 2016. Dopo una breve introduzione che illustra le modifiche importanti apportate all'architettura e alle dipendenze di sistema corrispondenti, descrive i requisiti software e di configurazione e fornisce un percorso di distribuzione consigliato per abilitare e verificare le funzionalità di Business Intelligence in tre fasi principali. Questo white paper presenta anche i problemi noti esistenti nelle versioni SharePoint Server 2016 Beta 2, Office Online Server Preview e SQL Server 2016 CTP 3.1 e suggerisce le soluzioni alternative appropriate. Queste soluzioni alternative non saranno necessarie nelle versioni finali dei prodotti. In fase di distribuzione delle versioni RTM verrà pubblicata una versione aggiornata di questo white paper.  
  
 **Autore:**Kay Unkroth, Jason Haak  
  
 **Revisori tecnici:** Adam Saxton, Anne Zorner, Craig Guyer, Frank Weigel, Gregory Appel, Heidi Steen, Kasper de Jonge, Kirk Stark, Klaus Sobel, Mike Plumley, Mike Taghizadeh, Patrick Wheeler, Riccardo Muti, Steve Hord  
  
 **Data di pubblicazione:**gennaio 2016  
  
 **Si applica a:** SQL Server 2016 CTP3.1, SharePoint 2016 Preview, Office Online Server Preview  
  
 Il documento [Deploying SQL Server 2016 PowerPivot and Power View in a Multi-Tier SharePoint 2016 Farm](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Deploying%20SQL%20Server%202016%20PowerPivot%20and%20Power%20View%20in%20a%20Multi-Tier%20SharePoint%202016%20Farm.docx) (Distribuzione di SQL Server 2016 PowerPivot e Power View in una farm di SharePoint 2016 a più livelli) è disponibile in formato Word.  
  
  
