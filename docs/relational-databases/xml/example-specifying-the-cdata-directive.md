---
title: 'Esempio: specifica della direttiva CDATA | Microsoft Docs'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CDATA directive
ms.assetid: 949071e6-787f-480d-bb86-3ac16a027af1
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cc5c0a1bcabf8a6e254570bc9b31ac69d59570bc
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="example-specifying-the-cdata-directive"></a>Esempio: specifica della direttiva CDATA
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] Se si specifica la direttiva **CDATA**, i dati contenuti non vengono codificati come entità, ma vengono inseriti nella sezione CDATA. Gli attributi **CDATA** devono essere privi di nome.  
  
 La query seguente riporta la descrizione di riepilogo del modello di prodotto in una sezione CDATA.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        '<Summary>This is summary description</Summary>'     
            as [ProductModel!1!!CDATA] -- no attribute name so ELEMENT assumed  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 Risultato:  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
   <![CDATA[<Summary>This is summary description</Summary>]]>  
</ProductModel>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo della modalità EXPLICIT con FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
