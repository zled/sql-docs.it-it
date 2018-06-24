---
title: Utilizzare il percorso completo per registrare i nomi DLL di stored procedure estesa | Documenti Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5735e7cc66f269a03ba37fc33dd59e1bdc46c7d1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065294"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a>Utilizzare il percorso completo per registrare i nomi delle DLL delle stored procedure estese
  Le stored procedure estese registrate precedentemente senza il percorso completo per il nome DLL possono non funzionare dopo l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Le stored procedure estese registrate precedentemente senza il percorso completo per il nome DLL possono non funzionare dopo l'aggiornamento, poiché la vecchia directory BINN non viene aggiunta al nuovo percorso durante il processo di aggiornamento. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può non essere in grado di trovare le stored procedure estese.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Prima di eseguire l'aggiornamento, attenersi alla procedura seguente per ogni stored procedure estesa non registrata utilizzando un percorso completo:  
  
1.  Per eliminare la stored procedure estesa eseguire sp_dropextendedproc.  
  
2.  Per registrare la stored procedure estesa con il percorso completo eseguire sp_addextendedproc.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
