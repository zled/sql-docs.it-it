---
title: Oggetto SqlXmlAdapter (classi gestite SQLXML) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3240c1e0d553bb0bdcc97d529dfee92d89332908
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlxml-managed-classes---sqlxmladapter-object"></a>-Classi gestite SQLXML oggetto SqlXmlAdapter
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Questo oggetto fornisce metodi che facilitano l'interazione con il set di dati in [!INCLUDE[msCoName](../../../includes/msconame-md.md)].NET Framework. Per un esempio funzionante, vedere [l'accesso a funzionalità SQLXML nell'ambiente .NET](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 Oggetto SqlXmlAdapter supporta questi metodi:  
  
 void Fill (DataSet ds)  
 Inserisce nel set di dati di .NET Framework i dati XML recuperati da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 void Update (DataSet ds)  
 Applica aggiornamenti ai record in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dai dati del set di dati.  
  
 Oggetto SqlXmlAdapter supporta questi costruttori:  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto SqlXmlCommand & #40; Gestite SQLXML classi & #41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md)   
 [Oggetto SqlXmlParameter & #40; Gestite SQLXML classi & #41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
