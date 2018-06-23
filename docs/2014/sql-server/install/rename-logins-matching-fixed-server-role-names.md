---
title: Rinominare gli account di accesso corrispondenti i nomi dei ruoli predefiniti del server | Documenti Microsoft
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
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 54223b28e681115df1b4ecf11f4fb96d13c68fd9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066630"
---
# <a name="rename-logins-matching-fixed-server-role-names"></a>Rinominare gli account di accesso con nomi uguali a quelli dei ruoli predefiniti del server
  Uno o più nomi di account di accesso definiti dall'utente sono uguali a nomi di ruoli predefiniti del server. I nomi dei ruoli predefiniti del server sono riservati. Prima di eseguire l'aggiornamento, rinominare gli account di accesso.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 I nomi dei ruoli predefiniti del server riportati di seguito sono riservati e non possono essere utilizzati come nomi di account di accesso definiti dall'utente:  
  
-   **sysadmin**  
  
-   **serveradmin**  
  
-   **setupadmin**  
  
-   **securityadmin**  
  
-   **processadmin**  
  
-   **dbcreator**  
  
-   **diskadmin**  
  
-   **bulkadmin**  
  
## <a name="corrective-action"></a>Azione correttiva  
 Prima di eseguire l'aggiornamento, completare i passaggi seguenti:  
  
1.  Registrare gli ID di sicurezza (SID) degli account di accesso eseguendo l'istruzione seguente.  
  
    ```  
    SELECT name, sid   
    FROM master.dbo.syslogins   
    WHERE name IN('sysadmin', 'serveradmin','setupadmin', 'securityadmin','processadmin', 'dbcreator','diskadmin','bulkadmin')  
    ```  
  
2.  Eliminare gli account di accesso.  
  
3.  Usare la **sp_addlogin** procedure di sistema per creare nuovi account di accesso. Specificare il SID restituito nel passaggio 1 il **@sid** parametro per ogni account di accesso corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
