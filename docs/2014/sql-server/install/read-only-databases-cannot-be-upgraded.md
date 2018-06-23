---
title: Non è possibile aggiornare i database di sola lettura | Documenti Microsoft
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
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 11f94ceed205d8984ed5a253e1d989211012f10f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170967"
---
# <a name="read-only-databases-cannot-be-upgraded"></a>Non è possibile aggiornare database di sola lettura
  Alcuni database di questa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non possono essere aggiornati.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 È stato rilevato un database di sola lettura. Per aggiornare il database, è necessario che sia accessibile in scrittura dal programma di installazione.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Quando non viene utilizzato il database, utilizzare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], o l'istruzione ALTER DATABASE per modificare il database in lettura / scrittura. Per impostare il database in lettura/scrittura, utilizzare l'istruzione seguente.  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 Per ulteriori informazioni sull'istruzione ALTER DATABASE, vedere l'argomento "ALTER DATABASE ([!INCLUDE[tsql](../../includes/tsql-md.md)])" argomento nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
