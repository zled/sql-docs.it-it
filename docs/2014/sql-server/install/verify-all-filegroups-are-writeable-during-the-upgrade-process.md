---
title: Verificare che tutti i filegroup siano scrivibili durante il processo di aggiornamento | Documenti Microsoft
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
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e73899dd36a6413a2e7cdd50254049d5fcdc52ae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054914"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a>Verificare che durante il processo di aggiornamento tutti i filegroup siano scrivibili
  È stato rilevato un database con uno o più filegroup di sola lettura. Prima dell'aggiornamento, è necessario che i filegroup di tutti i database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] siano impostati su READ_WRITE.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Utilizzare ALTER DATABASE per impostare il filegroup su READ_WRITE.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
