---
title: WITH ROWS non è supportata nelle istruzioni CREATE STATISTICS la modalità di compatibilità 90 o successiva | Documenti Microsoft
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
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9d509352d99cab9359e7ea222f5fb2d5d7e28075
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155898"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>Quando è attiva la modalità di compatibilità 90 o successiva la clausola WITH ROWS non è supportata nelle istruzioni CREATE STATISTICS
  Se si esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con modalità di compatibilità 90 o successiva, l'utilizzo di WITH ROWS nelle istruzioni CREATE STATISTICS non è supportato.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Modificare le istruzioni CREATE STATISTICS che includono WITH ROWS specificando WITH SAMPLE *numero* righe, oppure specificando altre opzioni conformi alla sintassi documentata. Per ulteriori informazioni, vedere l'argomento "CREATE STATISTICS (Transact-SQL) nella documentazione online di SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
