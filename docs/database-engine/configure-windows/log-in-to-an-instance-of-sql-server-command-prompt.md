---
title: "Log In to an Instance of SQL Server (Command Prompt) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "logins [SQL Server], named instance of SQL Server"
  - "log ins [SQL Server]"
  - "logins [SQL Server], default instance of SQL Server"
  - "command prompt [SQL Server], logins"
  - "accesso [SQL Server]"
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Log In to an Instance of SQL Server (Command Prompt)
  In questo argomento viene illustrato come eseguire il test di connettività a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzare l'utilità **sqlcmd** .  
  
##  <a name="SSMSProcedure"></a>  
  
#### Per accedere all'istanza predefinita di SQL Server  
  
1.  Al prompt dei comandi digitare il comando seguente per connettersi mediante l'autenticazione di Windows:  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### Per accedere a un'istanza denominata di SQL Server  
  
1.  Al prompt dei comandi digitare il comando seguente per connettersi mediante l'autenticazione di Windows:  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## Vedere anche  
 [Utilità sqlcmd](../../tools/sqlcmd-utility.md)   
 [Utilità osql](../../tools/osql-utility.md)  
  
  