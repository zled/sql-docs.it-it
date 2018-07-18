---
title: Rimuovere le istruzioni che eliminano oggetti di sistema | Microsoft Docs
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
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7bb577db82aae98356481657faa9bd76a0ab2a82
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161832"
---
# <a name="remove-statements-that-drop-system-objects"></a>Rimuovere le istruzioni che eliminano oggetti di sistema
  Sono state rilevate istruzioni che eliminano oggetti di sistema. Gli oggetti di sistema, incluse le stored procedure estese, vengono distribuiti in sola lettura **risorsa** (mssqlsystemresource) del database e non può essere eliminata. Modificare le applicazioni in modo da revocare o negare l'autorizzazione EXECUTE sugli oggetti di sistema.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Istruzioni quali DROP TABLE, DROP PROCEDURE e **sp_dropextendedproc** non può essere utilizzato per rimuovere gli oggetti di sistema, poiché questi oggetti vengono distribuiti in sola lettura **risorsa** database.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Rimuovere dalle applicazioni tutte le istruzioni che tentano di eliminare oggetti di sistema. Modificare le applicazioni in modo da revocare o negare l'autorizzazione EXECUTE sugli oggetti di sistema. In alternativa è possibile utilizzare uno degli strumenti Configurazione superficie di attacco per disabilitare alcuni di questi oggetti. Ad esempio, il **xp_cmdshell** stored procedure estesa può essere disabilitata o attivata tramite lo strumento Configurazione superficie di attacco.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
