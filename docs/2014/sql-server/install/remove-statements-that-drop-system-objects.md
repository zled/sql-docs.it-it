---
title: Rimuovere le istruzioni che eliminano oggetti di sistema | Documenti Microsoft
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
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4c017e6fedbc7fd994e5b2d2ca4de184a082da65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062336"
---
# <a name="remove-statements-that-drop-system-objects"></a>Rimuovere le istruzioni che eliminano oggetti di sistema
  Sono state rilevate istruzioni che eliminano oggetti di sistema. Gli oggetti di sistema, incluse le stored procedure estese, vengono distribuiti in sola lettura **risorse** (mssqlsystemresource) del database e non può essere eliminata. Modificare le applicazioni in modo da revocare o negare l'autorizzazione EXECUTE sugli oggetti di sistema.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Istruzioni quali DROP TABLE, DROP PROCEDURE e **sp_dropextendedproc** non è utilizzabile per rimuovere gli oggetti di sistema, poiché questi oggetti vengono distribuiti in sola lettura **risorse** database.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Rimuovere dalle applicazioni tutte le istruzioni che tentano di eliminare oggetti di sistema. Modificare le applicazioni in modo da revocare o negare l'autorizzazione EXECUTE sugli oggetti di sistema. In alternativa è possibile utilizzare uno degli strumenti Configurazione superficie di attacco per disabilitare alcuni di questi oggetti. Ad esempio, il **xp_cmdshell** stored procedure estesa può essere disabilitata o attivata tramite lo strumento Configurazione superficie di attacco.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
