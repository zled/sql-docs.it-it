---
title: Visualizzare una raccolta di XML Schema archiviata| Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
caps.latest.revision: "30"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c54c5a8f9246ee58fe6b07b5b728531863bd48d
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="view-a-stored-xml-schema-collection"></a>Visualizzazione di una raccolta di XML Schema archiviata
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] Dopo aver importato una raccolta di XML Schema tramite l'istruzione [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md), i componenti di schema vengono archiviati nei metadati. Per ricostruire la raccolta di XML Schema, è possibile usare la funzione intrinseca [xml_schema_namespace](../../t-sql/xml/xml-schema-namespace.md). Questa funzione restituisce un'istanza del tipo di dati **xml** .  
  
 Ad esempio, la query seguente restituisce una raccolta di XML Schema (`ProductDescriptionSchemaCollection`) dallo schema relazionale di produzione nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 Se si desidera visualizzare solo uno schema della raccolta di XML Schema, è possibile specificare una query XQuery sul risultato di tipo **xml** restituito dalla funzione `xml_schema_namespace`.  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 Ad esempio, la query seguente recupera le informazioni di XML Schema relative alla manutenzione e alla garanzia dei prodotti dalla raccolta di schemi `ProductDescriptionSchemaCollection` .  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 Per recuperare uno schema specifico dalla raccolta, è inoltre possibile passare lo spazio dei nomi di destinazione facoltativo come terzo parametro della funzione `xml_schema_namespace` , come illustrato nella query seguente:  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 Quando si crea una raccolta di XML Schema nel database tramite l'istruzione CREATE XML SCHEMA COLLECTION, i componenti di schema vengono archiviati nei metadati. Si noti che vengono archiviati solo i componenti di schema riconosciuti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Non vengono archiviati commenti, annotazioni o attributi non XSD. Dal punto di vista funzionale, pertanto, lo schema ricostruito dalla funzione **xml_schema_namespace** è equivalente allo schema originale, ma l'aspetto non sarà necessariamente identico. Ad esempio, non verranno visualizzati gli stessi prefissi dello schema originale. Lo schema restituito dalla funzione **xml_schema_namespace** usa **t** come prefisso per lo spazio dei nomi di destinazione e **ns1**, **ns2**e così via per gli altri spazi dei nomi.  
  
 Se si desidera mantenere una copia identica di XML Schema, è consigliabile salvarli in un file o in una tabella di database all'interno di una colonna di tipo **xml** .  
  
 La vista del catalogo [sys.xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md) restituisce anche informazioni sulle raccolte di XML Schema, che includono il nome, la data di creazione e il proprietario della raccolta.  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte di XML Schema &#40;SQL Server&#41;](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  
