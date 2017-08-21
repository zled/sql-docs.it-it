---
title: Accedere a un'istanza di SQL Server (prompt dei comandi) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e672ebb3b8c13a61f0ec2a061195f88ba7c751c4
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a>Log In to an Instance of SQL Server (Command Prompt)
  In questo argomento viene illustrato come eseguire il test di connettività a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzare l'utilità **sqlcmd** .  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-log-in-to-the-default-instance-of-sql-server"></a>Per accedere all'istanza predefinita di SQL Server  
  
1.  Al prompt dei comandi digitare il comando seguente per connettersi mediante l'autenticazione di Windows:  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### <a name="to-log-in-to-a-named-instance-of-sql-server"></a>Per accedere a un'istanza denominata di SQL Server  
  
1.  Al prompt dei comandi digitare il comando seguente per connettersi mediante l'autenticazione di Windows:  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità sqlcmd](../../tools/sqlcmd-utility.md)   
 [Utilità osql](../../tools/osql-utility.md)  
  
  
