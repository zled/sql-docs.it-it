---
title: "Esempio: ridenominazione dell'elemento &lt;row&gt; | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f339d18e2653897cbc956bb605e60ebf8154dc40
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244761"
---
# <a name="example-renaming-the-ltrowgt-element"></a>Esempio: ridenominazione dell'elemento &lt;row&gt;
  Nella modalità RAW viene creato un elemento `<row>`per ogni riga del set di risultati. È possibile specificare un nome diverso per l'elemento impostando un argomento facoltativo per la modalità RAW, come illustrato nella query seguente. La query restituisce un elemento <`ProductModel`> per ogni riga del set di righe.  
  
## <a name="example"></a>Esempio  
  
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
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo della modalità RAW con FOR XML](use-raw-mode-with-for-xml.md)  
  
  
