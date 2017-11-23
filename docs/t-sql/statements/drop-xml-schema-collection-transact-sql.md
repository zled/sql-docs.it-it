---
title: DROP XML SCHEMA COLLECTION (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 11/25/2015
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP XML SCHEMA COLLECTION
- DROP_XML_SCHEMA_COLLECTION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- deleting XML schema collections
- XML schema collections [SQL Server], removing
- schema collections [SQL Server], removing
- removing XML schema collections
- dropping XML schema collections
- DROP XML SCHEMA COLLECTION statement
ms.assetid: d686f2f5-e03a-4ffe-a566-6036628f46f1
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d490d246e295f3d01478c7ffaec57efd7afa739d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="drop-xml-schema-collection-transact-sql"></a>DROP XML SCHEMA COLLECTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina l'intera raccolta di XML Schema e tutti i relativi componenti.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP XML SCHEMA COLLECTION [ relational_schema. ]sql_identifier  
```  
  
## <a name="arguments"></a>Argomenti  
 *relational_schema*  
 Identifica il nome dello schema relazionale. Se viene omesso, viene utilizzato lo schema relazionale predefinito.  
  
 *sql_identifier*  
 Nome della raccolta di XML Schema da rimuovere.  
  
## <a name="remarks"></a>Osservazioni  
 La rimozione di una raccolta di XML Schema è un'operazione transazionale. Ciò significa che quando si rimuove una raccolta di XML Schema all'interno di una transazione e successivamente si esegue il rollback della transazione, la raccolta di XML Schema non viene rimossa.  
  
 Non è possibile rimuovere una raccolta di XML Schema quando è in uso e pertanto la raccolta da rimuovere non può essere:  
  
-   Associato a una **xml** tipo di parametro o una colonna.  
  
-   Specificato in un vincolo di tabella.  
  
-   Contenuto in un riferimento di una stored procedure o funzione associata a uno schema. Ad esempio, la funzione seguente bloccherà la raccolta di XML Schema `MyCollection` poiché viene specificato `WITH SCHEMABINDING`. Se si rimuove tale specifica, verrà rimosso il blocco su XML SCHEMA COLLECTION.  
  
    ```  
    CREATE FUNCTION dbo.MyFunction()  
    RETURNS int  
    WITH SCHEMABINDING  
    AS  
    BEGIN  
       ...  
       DECLARE @x XML(MyCollection)  
       ...  
    END;  
    ```  
  
## <a name="permissions"></a>Permissions  
 Per rimuovere una raccolta XML SCHEMA COLLECTION è richiesta l'autorizzazione DROP per la raccolta.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come rimuovere una raccolta di XML Schema.  
  
```  
DROP XML SCHEMA COLLECTION ManuInstructionsSchemaCollection;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREARE una raccolta di XML SCHEMA &#40; Transact-SQL &#41;](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [Istruzione ALTER XML SCHEMA COLLECTION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-xml-schema-collection-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Confronto dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Requisiti e limitazioni per le raccolte di XML Schema nel server](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
