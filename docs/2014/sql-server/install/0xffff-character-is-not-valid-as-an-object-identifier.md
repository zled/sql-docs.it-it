---
title: il carattere 0xFFFF non è valido come identificatore di oggetto | Documenti Microsoft
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
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ded2cd54bced9ae69e207a1b609688c2fcf3b633
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069748"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a>Il carattere 0xFFFF non è valido come identificatore di oggetto
  È stato rilevato un identificatore di oggetto contenente il carattere 0xFFFF. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive non è possibile rinominare o fare riferimento a oggetti quali database, tabelle e colonne con identificatori contenenti tale carattere nella modalità di compatibilità del database 90 o successiva. Quando si esegue l'aggiornamento a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], la modalità di compatibilità dei database utente non cambia. Prima di impostare la modalità di compatibilità del database 90 o successiva, rinominare l'oggetto che contiene il carattere 0xFFFF.  
  
 Per ulteriori informazioni sugli identificatori, vedere "Identificatori" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni sulle modalità compatibilità del database, vedere "sp_dbcmptlevel" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
