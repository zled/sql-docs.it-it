---
title: "Xs:Tipo QName | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Xs:Tipo QName"
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# Xs:Tipo QName
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta tipi derivati da **xs:QName** a causa dell'utilizzo di un elemento di restrizione di XML Schema. Attualmente, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta tipi unione con **QName** come tipo di membro.  
  
## Esempio  
 Le seguenti istruzioni `CREATE XML SCHEMA COLLECTION` non permettono di caricare l'elemento XML Schema, in quanto specificano il tipo `xs:QName` come tipo di membro dell'unione:  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 Entrambe le istruzioni hanno esito negativo e generano un errore.  
  
## Vedere anche  
 [Requisiti e limitazioni per l'utilizzo di raccolte di XML Schema nel server](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  