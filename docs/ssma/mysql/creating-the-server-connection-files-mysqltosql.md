---
title: Creazione dei file di connessione del Server (MySQLToSQL) | Documenti Microsoft
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
helpviewer_keywords:
- Server connection file validation
- Server connection files
ms.assetid: df0e970c-da0b-4118-b359-c9dcbbad16d6
caps.latest.revision: 18
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9aa45d743a62fb3c2a111b64e254c78db22a7e90
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="creating-the-server-connection-files-mysqltosql"></a>Creazione dei file di connessione del Server (MySQLToSQL)
Nella sezione del file di script server o in un file di connessione server separato, è possibile specificare le informazioni sul server. Il parametro della riga di comando per il file di connessione del server è, `-c <serverconnectionfile>`. Se lo stesso id di server è presente nel file di connessione del server sia file di script, è considerata la definizione del server nel file di script.  
  
**Esempio:**  
  
```xml  
<!--Sample of server connection file commands -->  
  
<mysql name ="<source-server-unique-name>">  
  
   <standard-mode>  
  
      <server value ="<server-name>"/>  
  
      <user-id value ="<user-name>"/>  
  
      <password value ="<password>"/>  
  
      <port value ="<port>"/>  
  
   </standard-mode>  
  
</mysql>  
```  
  
```xml  
<!--Connection to SQL Server-->  
  
<sql-server name="<target-server-unique-name>">  
  
   <sql-server-authentication>  
  
      <server value="<server-name>"/>  
  
      <database value="<database-name>"/>  
  
      <user-id value="<user-name>"/>  
  
      <password value="<password>"/>  
  
      <encrypt value="<true/false>"/>  
  
      <trust-server-certificate value="<true/false>"/>  
  
   </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="<target-server-unique-name>">  
  
   <server value="<server-name>"/>  
  
   <database value="<database-name>"/>  
  
   <user-id value="<user-name>"/>  
  
   <password value="<password>"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>Convalida del File di connessione di server  
L'utente può facilmente convalidare il file di connessione del server nel file di definizione dello schema **'M2SSConsoleScriptServersSchema.xsd'** disponibile nella cartella 'Schemi'.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo nella console di gestione è [in esecuzione la Console di SSMA &#40; MySQLToSQL &#41;](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[L'esecuzione la Console SSMA (MySQL)](http://msdn.microsoft.com/en-us/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
