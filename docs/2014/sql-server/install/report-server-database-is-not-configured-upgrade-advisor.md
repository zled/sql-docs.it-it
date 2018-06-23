---
title: Database del server di report non è configurato (Upgrade Advisor) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: f86e9963750d2bacbdc55e235e4975a05c2f625e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070195"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a>Il database del server di report non è configurato (Upgrade Advisor)
  L'aggiornamento è bloccato a causa di una configurazione del server di report incompleta. Il database del server di report non è configurato.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  Modalità nativa di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] &#124; Modalità SharePoint di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 L'installazione può aggiornare solo un'istanza del server di report completamente configurata. Per continuare, è necessario configurare il database del server di report o utilizzare Microsoft Windows **Pannello di controllo** per rimuovere funzionalità da server di report il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione. Dopo la rimozione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è possibile aggiornare gli altri componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Azione correttiva  
 Se il database del server di report non è stato configurato, il server di report non è operativo e deve essere rimosso prima dell'aggiornamento.  
  
 Per ulteriori informazioni sulla disinstallazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vedere [disinstallare Reporting Services 2012](http://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\)). Nell'argomento viene descritto come disinstallare una versione specifica e le procedure sono simili a quelle delle versioni precedenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento di Reporting Services &#40;Preparazione aggiornamento&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  