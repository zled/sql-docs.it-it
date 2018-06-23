---
title: Le query FOR XML AUTO restituiscono riferimenti a tabelle derivate nella modalità di compatibilità 90 o successiva | Documenti Microsoft
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
- FOR XML AUTO [SQL Server]
ms.assetid: 10c32f06-f7e1-40e0-8f79-6d921f2bef1d
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a056ae122c30b6014d325e4e87a43921426905c4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062797"
---
# <a name="for-xml-auto-queries-return-derived-table-references-in-90-or-later-compatibility-modes"></a>In modalità di compatibilità 90 o successiva le query FOR XML AUTO restituiscono riferimenti a tabelle derivate
  Quando il livello di compatibilità del database è impostato su 90 o successivo, le query FOR XML eseguite in modalità AUTO restituiscono riferimenti ad alias di tabelle derivate. Quando il livello di compatibilità è impostato su 80, le query FOR XML AUTO restituiscono riferimenti alle tabelle di base che definiscono una tabella derivata.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Si consideri ad esempio la tabella seguente:  
  
```  
CREATE TABLE Test(id int);  
INSERT INTO Test VALUES(1);  
INSERT INTO Test VALUES(2);  
```  
  
 La query seguente, che include una tabella derivata, produce risultati diversi con i livelli di compatibilità 80, 90 o successivo:  
  
```  
SELECT * FROM   
   (SELECT a.id AS a, b.id AS b   
    FROM Test a JOIN Test b ON a.id=b.id)  
AS DerivedTest   
FOR XML AUTO;  
```  
  
 Con il livello di compatibilità 80, la query restituisce i risultati seguenti. I risultati fanno riferimento agli alias delle tabelle di base `a` e `b` della tabella derivata anziché all'alias della tabella derivata.  
  
```  
<a a="1"><b b="1"/></a><a a="2"><b b="2"/></a>  
```  
  
 Con il livello di compatibilità 90 o successivo, la query restituisce i riferimenti all'alias della tabella derivata `DerivedTest` anziché alle tabelle di base della tabella derivata.  
  
```  
<DerivedTest a="1" b="1"/><DerivedTest a="2" b="2"/>  
```  
  
## <a name="corrective-action"></a>Azione correttiva  
 Apportare le modifiche necessarie all'applicazione in base alle modifiche dei risultati delle query FOR XML AUTO che includono tabelle derivate e che vengono eseguite con il livello di compatibilità 90 o successivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
