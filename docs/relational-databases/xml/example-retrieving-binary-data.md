---
title: 'Esempio: recupero di dati binari | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9b2031a25b80e69a77a2e07dcab23bb03d1fc3fe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601549"
---
# <a name="example-retrieving-binary-data"></a>Esempio: recupero di dati binari
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  La query seguente restituisce la foto del prodotto archiviata in una colonna di tipo **varbinary(max)** . L'opzione `BINARY BASE64` specificata nella query consente di restituire i dati binari nel formato con codifica Base64.  
  
## <a name="example"></a>Esempio  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductPhotoID, ThumbNailPhoto  
FROM Production.ProductPhoto  
WHERE ProductPhotoID=1  
FOR XML RAW, BINARY BASE64 ;  
GO  
```  
  
 Risultato:  
  
```  
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo della modalità RAW con FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
