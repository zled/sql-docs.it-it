---
title: Rimuovere le istruzioni che modificano oggetti di sistema | Documenti Microsoft
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
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c77525957fa679659a67bfa41f28090e028a7a2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069534"
---
# <a name="remove-statements-that-modify-system-objects"></a>Rimuovere le istruzioni che modificano oggetti di sistema
  Sono state rilevate istruzioni che aggiornano il catalogo di sistema. Gli aggiornamenti diretti del catalogo di sistema non sono consentiti. Modificare gli script SQL in modo che utilizzino API ufficiali e documentate.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Gli aggiornamenti diretti del catalogo di sistema non sono consentiti. Qualsiasi tentativo di eseguire questa operazione restituirà l'errore seguente:  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a>Azione correttiva  
 Modificare gli script SQL in modo che utilizzino API ufficiali e documentate. Ad esempio, utilizzare ALTER DATABASE *database_name* SET EMERGENCY anziché eseguire un'istruzione UPDATE sul **sysdatabases** tabella di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
