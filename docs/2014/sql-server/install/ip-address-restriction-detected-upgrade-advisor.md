---
title: Restrizione degli indirizzi IP rilevata (Upgrade Advisor) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: b3ab784e15737a08b9bf928d6d15e08a27636b88
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065976"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a>Rilevata restrizione degli indirizzi IP (Upgrade Advisor)
  Sono state rilevate una o più restrizioni degli indirizzi IP sul sito Web di IIS che ospita le directory virtuali del server di report o di Gestione report. In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è disponibile il supporto nativo per le restrizioni degli indirizzi IP.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Nativo.|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Non è possibile definire le restrizioni degli indirizzi IP sugli URL creati per un server di report aggiornato. L'aggiornamento può continuare, ma le restrizioni degli indirizzi IP non saranno definite sugli URL di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="corrective-action"></a>Azione correttiva  
 Dopo l'aggiornamento, utilizzare ISA Server, il software del firewall o un'altra soluzione per consentire o escludere richieste dagli indirizzi IP specifici al server di report.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento di Reporting Services &#40;Preparazione aggiornamento&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  