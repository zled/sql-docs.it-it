---
title: Nuova colonna nell'output di sp_helptrigger potrebbe influire sulle applicazioni | Documenti Microsoft
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
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d62b9b9546fa113557bf962d68876d8c55a71ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064830"
---
# <a name="new-column-in-output-of-sphelptrigger-may-impact-applications"></a>La nuova colonna nell'output di sp_helptrigger potrebbe influire sulle applicazioni
  stored procedure di trigger_schemaias l'ultima colonna nel set di risultati restituita dal sistema sp_helptrigger.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Per ottenere informazioni sui trigger definiti in una specifica tabella, eseguire una query sulla vista del catalogo sys.triggers.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Esaminare l'utilizzo di sp_helptrigger nelle applicazioni. Può essere necessario modificare le applicazioni in modo da gestire la colonna aggiuntiva. In alternativa, è possibile utilizzare invece la vista del catalogo sys. Triggers.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
