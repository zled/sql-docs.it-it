---
title: WITH ROWS non è supportata nelle istruzioni CREATE STATISTICS in modalità di compatibilità 90 o successiva | Microsoft Docs
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
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 98aec243141e642cd0ef77719795490a1333f473
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37294091"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>Quando è attiva la modalità di compatibilità 90 o successiva la clausola WITH ROWS non è supportata nelle istruzioni CREATE STATISTICS
  Se si esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con modalità di compatibilità 90 o successiva, l'utilizzo di WITH ROWS nelle istruzioni CREATE STATISTICS non è supportato.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Modificare le istruzioni CREATE STATISTICS che includono WITH ROWS specificando WITH SAMPLE *numero* righe, oppure specificando altre opzioni conformi alla sintassi documentata. Per ulteriori informazioni, vedere l'argomento "CREATE STATISTICS (Transact-SQL) nella documentazione online di SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
