---
title: 'Esempio: recupero delle informazioni relative al modello del prodotto in formato XML | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving XML information example
ms.assetid: 3828b4ca-3ab2-444f-9c58-8be6e7f064a6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4ec7ed358ab8c6c5f42e378a23dd4ba911800ae3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219881"
---
# <a name="example-retrieving-product-model-information-as-xml"></a>Esempio: recupero delle informazioni relative al modello del prodotto in formato XML
  La query seguente restituisce le informazioni relative al modello del prodotto. `RAW` la modalità è specificata nella clausola `FOR XML` .  
  
## <a name="example"></a>Esempio  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW;  
GO  
```  
  
 Risultato parziale:  
  
 `<row ProductModelID="122" Name="All-Purpose Bike Stand" />`  
  
 `<row ProductModelID="119" Name="Bike Wash" />`  
  
 Per recuperare il codice XML incentrato sugli elementi, è necessario specificare la direttiva `ELEMENTS` .  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 Risultato:  
  
```  
<row>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</row>  
<row>  
  <ProductModelID>119</ProductModelID>  
  <Name>Bike Wash</Name>  
</row>  
```  
  
 È possibile specificare facoltativamente il `TYPE` direttiva per recuperare i risultati come `xml` tipo. La direttiva `TYPE` non modifica il contenuto dei risultati. Solo il tipo di dati dei risultati viene modificato.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, TYPE ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo della modalità RAW con FOR XML](use-raw-mode-with-for-xml.md)  
  
  
