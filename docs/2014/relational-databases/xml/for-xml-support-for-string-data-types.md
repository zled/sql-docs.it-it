---
title: Supporto di FOR XML per i tipi di dati stringa | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- strings [SQL Server], XML
ms.assetid: bf069da8-de1e-44d2-a1fb-ade383076ac1
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3f29a28e4b8d6105c84200d0993dbce7b754cbd5
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889167"
---
# <a name="for-xml-support-for-string-data-types"></a>Supporto di FOR XML per i tipi di dati stringa
  Il codice XML generato dagli spazi vuoti FOR XML nei dati viene sostituito con delle entità.  
  
 Nell'esempio seguente viene creata la tabella **T** e vengono inseriti dati di esempio che includono i caratteri di avanzamento riga, ritorno a capo e tabulazione. L'istruzione SELECT recupera i dati dalla tabella.  
  
```  
CREATE TABLE T  
(  
  c1 int identity primary key,  
  c2 varchar(100)  
);  
go  
  
INSERT T (c2) VALUES ('Special character 0xD for carriage return ' + convert(varchar(10), 0xD) + ' after carriage return');  
INSERT T (c2) VALUES ('Special character 0x9 for tab ' + convert(varchar(10), 0x9) + ' after tab' );  
INSERT T (c2) VALUES ('Special character 0xA for line feed ' + convert(varchar(10), 0xA) + ' after line feed');  
go  
SELECT *   
FROM T  
FOR XML AUTO;  
go  
```  
  
 Risultato:  
  
```  
 <T c1="1" c2="Special character 0xD for carriage return   
 after carriage return" />  
 <T c1="2" c2="Special character 0x9 for tab     after tab" />  
 <T c1="3" c2="Special character 0xA for line feed   
after line feed" />  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il carattere di ritorno a capo nella prima riga viene sostituito con l'entità &#xD.  
  
-   Il carattere di tabulazione nella seconda riga viene sostituito con l'entità &#x09.  
  
-   Il carattere di avanzamento riga nella terza riga viene sostituito con l'entità &#xA.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di FOR XML per vari tipi di dati di SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  
