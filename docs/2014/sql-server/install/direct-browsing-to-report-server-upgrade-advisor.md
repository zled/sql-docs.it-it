---
title: Esplorazione diretta nel Server di Report (Upgrade Advisor) di | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: f08bc5d25eed160b814bfcdc255e1f198836da2b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055399"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>Esplorazione diretta nel server di report (Upgrade Advisor)
  Upgrade Advisor ha rilevato l'installazione corrente di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] durante l'esplorazione direttamente per la directory virtuale del server di report.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modalità SharePoint.|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Upgrade Advisor ha rilevato l'installazione corrente di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] durante l'esplorazione direttamente alla directory virtuale di server di report, ad esempio **http://\<nome server > / ReportServer**. Non è supportato nelle versioni correnti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  La regola costituisce un avviso e l'aggiornamento non viene bloccato.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Sfogliare il modello utilizzando l'interfaccia utente di SharePoint per le raccolte documenti o utilizzare **http://\<nome server > / sito di sharepoint vti_bin/reportserver**.  
  
  