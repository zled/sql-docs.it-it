---
title: Certificati client sul sito web server di report (Upgrade Advisor) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 93128f60320fbcf82a3368d6008fe647497fa4dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37270287"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a>Certificati client sul sito Web del server di report (Upgrade Advisor)
  Sono stati rilevati uno o più certificati client sul sito Web IIS che ospita le directory virtuali del server di report o di Gestione report.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non supporta l'utilizzo di certificati client per l'autenticazione degli utenti. L'aggiornamento può continuare, ma i certificati client non verranno utilizzati dal server di report aggiornato.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Sarà necessario utilizzare una soluzione distinta, ad esempio ISA Server, per assicurarsi di rispettare i requisiti di autenticazione dei certificati client.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento di Reporting Services &#40;Preparazione aggiornamento&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
