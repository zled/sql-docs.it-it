---
title: Programma di formattazione XML sul lato server (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- server-side XML formatting
ms.assetid: ae9ea068-0857-4505-a3b2-f53d256b644c
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: c7c32468545c500383601a5b19f8693d73f6905e
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39534461"
---
# <a name="server-side-xml-formatting-sqlxml-40"></a>Formattazione XML sul lato server (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In questo argomento sono incluse informazioni sulla formattazione di documenti XML sul lato server dai set di righe generati da query eseguite su un database in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è possibile archiviare e recuperare documenti XML da e verso tabelle di database. Per recuperare un documento XML, utilizzare l'estensione della query FOR XML in una query SELECT.  
  
 Si supponga ad esempio un'applicazione client esegue un comando sul [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] costituito da quanto segue [!INCLUDE[tsql](../../../includes/tsql-md.md)] query:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML AUTO  
```  
  
 Il server esegue la query in due passaggi. Il server esegue innanzitutto l'istruzione SELECT seguente:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 Il server applica quindi la trasformazione FOR XML al set di righe generato. Il documento XML risultante viene quindi inviato al client come set di righe a una colonna. In questa documentazione questo processo viene definito formattazione XML sul lato server.  
  
 Sul lato server è possibile specificare le modalità seguenti con una clausola FOR XML:  
  
-   RAW  
  
-   AUTO  
  
-   EXPLICIT  
  
 Per altre informazioni sulla clausola FOR XML, vedere [costruzione XML utilizzando FOR XML](../../../relational-databases/xml/for-xml-sql-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura della formattazione XML sul lato Client e lato Server &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/architecture-of-client-side-and-server-side-xml-formatting-sqlxml-4-0.md)   
 [Formattazione XML sul lato client &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)   
 [FOR XML &#40;SQL Server&#41;](../../../relational-databases/xml/for-xml-sql-server.md)  
  
  
