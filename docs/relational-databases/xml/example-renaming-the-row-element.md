---
title: "Esempio: ridenominazione dell&#39;elemento &lt;row&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modalità RAW, ridenominazione esempio <row>"
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# Esempio: ridenominazione dell&#39;elemento &lt;row&gt;
  Nella modalità RAW viene creato un elemento `<row>` per ogni riga del set di risultati. È possibile specificare un nome diverso per l'elemento impostando un argomento facoltativo per la modalità RAW, come illustrato nella query seguente. La query restituisce un elemento <`ProductModel`> per ogni riga del set di righe.  
  
## Esempio  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 Di seguito è riportato il risultato. Nella query viene aggiunta la direttiva `ELEMENTS` e pertanto il risultato è incentrato sugli elementi.  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## Vedere anche  
 [Utilizzo della modalità RAW con FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  