---
title: 'Esempio: specifica di XSINIL con la direttiva ELEMENTS | Microsoft Docs'
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
- RAW mode, specifying XSINIL example
ms.assetid: 07c873ff-1f9d-480e-8536-862c39eb8249
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 35f2a9ee4494805d9c451a0f03357acd3cc47dc4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37318001"
---
# <a name="example-specifying-xsinil-with-the-elements-directive"></a>Esempio: specifica di XSINIL con la direttiva ELEMENTS
  Nella query seguente viene specificata la direttiva `ELEMENTS` per generare codice XML incentrato sugli elementi dai risultati della query.  
  
## <a name="example"></a>Esempio  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 Di seguito è riportato il risultato parziale.  
  
```  
<row>  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
 Nella colonna `Color` sono presenti i valori Null per alcuni prodotti e pertanto nel codice XML risultante non verrà generato l'elemento <`Color`> corrispondente. Se si aggiunge la direttiva `XSINIL` insieme a `ELEMENTS`, è possibile generare l'elemento <`Color`> anche per i valori Null relativi al colore nel set dei risultati.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS XSINIL ;  
```  
  
 Risultato parziale:  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
  <Color xsi:nil="true" />  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo della modalità RAW con FOR XML](use-raw-mode-with-for-xml.md)  
  
  
