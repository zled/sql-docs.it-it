---
title: Creazione dei file di connessione del Server (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 829153be-aa8e-4162-87e8-69882feecf19
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 333640f0b258c97ba87c56fe4bd8a15100bba858
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="creating-the-server-connection-files-accesstosql"></a>Creazione dei file di connessione del Server (AccessToSQL)
Nella sezione del file di script server o in un file di connessione server separato, è possibile specificare le informazioni sul server. Il parametro della riga di comando per il file di connessione del server è, `-c <serverconnectionfile>`. Se lo stesso id di server è presente nel file di connessione del server sia file di script, è considerata la definizione del server nel file di script.  
  
```xml  
<!--Sample of server connection file commands -->  
<!--Connection to SQL Server-->  
  
<sql-server name="target_3">  
  
  <sql-server-authentication>  
  
    <server value="$TargetServerName$"/>  
  
    <database value="$TargetDB$"/>  
  
    <user-id value="$TargetUserName$"/>  
  
    <password value="$TargetPassword$"/>  
  
    <encrypt value="true"/>  
  
    <trust-server-certificate value="true"/>  
  
  </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="target_azure">  
  
  <server value="$TargetAzureServerName$"/>  
  
  <database value="$TargetAzureDB$"/>  
  
  <user-id value="$TargetAzureUserName$"/>  
  
  <password value="$TargetAzurePassword$"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>Convalida del File di connessione di server  
L'utente può facilmente convalidare il file di connessione del server nel file di definizione dello schema **'A2SSConsoleScriptServersSchema.xsd'** disponibile nella cartella 'Schemi'.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo nella console di gestione è [in esecuzione la Console di SSMA &#40; AccessToSQL &#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[L'esecuzione la Console SSMA (accesso)](http://msdn.microsoft.com/en-us/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  

