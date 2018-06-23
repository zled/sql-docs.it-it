---
title: PER l'esplorazione non è consentita nelle viste nella modalità di compatibilità 90 o successiva | Documenti Microsoft
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
- views [SQL Server], FOR BROWSE clause
- FOR BROWSE clause
ms.assetid: 8f49b1c1-d877-4c46-b988-f8cdd8ac0925
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 87a937dafea15fdc9eca3bbbafbacc17275374b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069965"
---
# <a name="for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes"></a>FOR BROWSE non consentita nelle viste in modalità di compatibilità 90 o successiva
  È stata rilevata la clausola FOR BROWSE in una vista. La clausola FOR BROWSE è consentita (e ignorata) nelle viste se la modalità di compatibilità del database è impostata su 80. Se è impostata la modalità di compatibilità 90 o successiva, la clausola FOR BROWSE non è consentita nelle viste.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Quando si esegue l'aggiornamento, la modalità di compatibilità dei database utente non cambia. Prima di impostare la modalità di compatibilità del database su 90 o successiva, rimuovere la clausola FOR BROWSE dalle definizioni di viste. Per ulteriori informazioni, vedere "sp_dbcmptlevel" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
