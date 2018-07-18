---
title: Rimuovere le istruzioni che modificano le autorizzazioni a livello di colonna per oggetti di sistema | Microsoft Docs
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
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 217feecec3058c71a51914bde1db9e20755472db
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316121"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a>Rimuovere le istruzioni che modificano le autorizzazioni a livello di colonna per gli oggetti di sistema
  Sono state rilevate autorizzazioni non standard a livello di colonna per alcuni oggetti di sistema. Tali modifiche alle autorizzazioni non verranno mantenute durante l'aggiornamento. Le autorizzazioni a livello di colonna per gli oggetti di sistema non sono inoltre più supportate. Rimuovere dalle applicazioni tutte le istruzioni che impostano autorizzazioni a livello di colonna per oggetti di sistema.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Rimuovere dalle applicazioni le istruzioni che concedono, negano o revocano autorizzazioni a livello di colonna per oggetti di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
