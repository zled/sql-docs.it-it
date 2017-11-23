---
title: XML (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_TSQL
- xml
dev_langs: TSQL
helpviewer_keywords: xml data type [SQL Server], about xml data type
ms.assetid: 9198f671-8e61-4ca4-9c3a-859f84020e62
caps.latest.revision: "35"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 7dd987cd38c6f4b15e965b2510f7ae91b667a43a
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="xml-transact-sql"></a>xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Tipo di dati in cui vengono archiviati i dati XML. È possibile archiviare **xml** istanze in una colonna o una variabile di **xml** tipo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
xml ( [ CONTENT | DOCUMENT ] xml_schema_collection )  
```  
  
## <a name="arguments"></a>Argomenti  
 CONTENT  
 Limita il **xml** istanza da un frammento XML ben formato. I dati XML possono contenere più 0 (zero) o più elementi al livello principale. Al livello principale sono inoltre consentiti nodi di testo.  
  
 Questo è il comportamento predefinito.  
  
 DOCUMENT  
 Limita il **xml** istanza da un documento XML ben formato. I dati XML devono disporre di un unico elemento radice. Al livello principale non sono consentiti nodi di testo.  
  
 *xml_schema_collection*  
 Nome di una raccolta di XML Schema. Per creare un oggetto tipizzato **xml** colonna o variabile, è possibile specificare facoltativamente il nome della raccolta XML schema. Per ulteriori informazioni sui dati XML tipizzati e, vedere [confrontare dati XML tipizzati con dati XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="remarks"></a>Osservazioni  
 La rappresentazione archiviata delle **xml** le istanze di tipi di dati non possono superare 2 gigabyte (GB) di dimensioni.  
  
 I facet CONTENT e DOCUMENT sono applicabili soltanto a XML tipizzato. Per ulteriori informazioni vedere [confrontare dati XML tipizzati con dati XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="examples"></a>Esempi  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @y xml (Sales.IndividualSurveySchemaCollection);  
SET @y =  (SELECT TOP 1 Demographics FROM Sales.Individual);  
SELECT @y;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Conversione tipo di dati &#40; motore di Database &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [metodi con tipo di dati XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  
