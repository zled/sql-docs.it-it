---
title: WITH CHECK OPTION non è supportata nelle viste che contengono TOP nella modalità di compatibilità 90 o successiva | Documenti Microsoft
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
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0dde9e879d278455544d4f323a8f3ffdd492760d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054683"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a>WITH CHECK OPTION non è supportata nelle viste che contengono TOP nella modalità di compatibilità 90 o successiva
  È presente una vista definita utilizzando la clausola WITH CHECK OPTION e una clausola TOP nell'istruzione SELECT della vista o in una vista a cui fa riferimento. In modalità di compatibilità del database 80 e precedenti, le viste definite in questo modo consentono la modifica dei dati tramite la vista. Questo comportamento non è corretto e può dare luogo a risultati non accurati. I dati non possono essere inseriti o aggiornati tramite una vista che utilizza una clausola WITH CHECK OPTION se tale vista o una vista a cui fa riferimento utilizza la clausola TOP e la modalità di compatibilità del database è 90 o successiva.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Quando si esegue l'aggiornamento, la modalità di compatibilità dei database utente non cambia. Prima di impostare la modalità di compatibilità del database su 100 o successiva, modificare le viste che utilizzano le clausole WITH CHECK OPTION e TOP se è richiesta la modifica di dati tramite la vista. Per altre informazioni, vedere [sp_dbcmptlevel &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
