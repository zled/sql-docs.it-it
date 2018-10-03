---
title: 'Esempio: recupero di dati binari | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3ebfd863d458231c802f3648e3a53411f13f8bed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48144021"
---
# <a name="example-retrieving-binary-data"></a>Esempio: recupero di dati binari
  La query seguente restituisce la foto del prodotto archiviata in una colonna di tipo `varbinary(max)`. L'opzione `BINARY BASE64` specificata nella query consente di restituire i dati binari nel formato con codifica Base64.  
  
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
 [Utilizzo della modalità RAW con FOR XML](use-raw-mode-with-for-xml.md)  
  
  
