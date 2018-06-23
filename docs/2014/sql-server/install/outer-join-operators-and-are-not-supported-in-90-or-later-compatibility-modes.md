---
title: Operatori outer join *= e =* non sono supportati nella modalità di compatibilità 90 o successiva | Documenti Microsoft
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
- outer joins
- =* join
- '*= join'
- joins [SQL Server]
ms.assetid: ca4aa11f-1048-411f-9c6c-3d0a8e319f2f
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47a58b60ecd303b893e001663134d9b510bbabfa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170494"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a>Operatori outer join *= e =* non sono supportati nella modalità di compatibilità 90 o successiva
  Upgrade Advisor ha rilevato l'utilizzo di operatori outer join * = e =\*. Tali operatori non sono supportati nella modalità di compatibilità 90 o successiva Quando si esegue l'aggiornamento, la modalità di compatibilità dei database utente non cambia. Le istruzioni in cui sono utilizzati questi operatori non riusciranno.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Prima di impostare la modalità di compatibilità del database su 90 o successiva, modificare le istruzioni che utilizzano gli operatori outer join * = e =\* utilizzare le parole chiave OUTER JOIN equivalenti. Nell'esempio seguente vengono illustrate una query che utilizza l'operatore `*=` e una query equivalente che utilizza le parole chiave `LEFT OUTER JOIN`.  
  
```  
-- This query uses an old-style outer join operator.  
USE pubs  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee, jobs   
WHERE employee.job_id *= jobs.job_id  
ORDER BY employee.job_id  
  
-- This query uses the ANSI standard keywords LEFT OUTER JOIN.  
USE pubs;  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
ORDER BY employee.job_id  
```  
  
 Per ulteriori informazioni sugli outer join, vedere "Utilizzo di outer join" nella documentazione online di SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
