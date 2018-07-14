---
title: Creare viste su colonne XML | Microsoft Docs
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
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3f575b1a21efa30d2317cff644b65c73150c4ac1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37170182"
---
# <a name="create-views-over-xml-columns"></a>Creazione di viste
  È possibile usare un `xml` colonna di tipo per creare visualizzazioni. L'esempio seguente crea una vista in cui il valore da un `xml` colonna di tipo viene recuperato utilizzando il `value()` metodo il `xml` tipo di dati.  
  
```  
-- Create the table.  
CREATE TABLE T (  
    ProductID          int primary key,   
    CatalogDescription xml)  
GO  
-- Insert sample data.  
INSERT INTO T values(1,'<ProductDescription ProductID="1" ProductName="SomeName" />')  
GO  
-- Create view (note the value() method used to retrieve ProductName   
-- attribute value from the XML).  
CREATE VIEW MyView AS   
  SELECT ProductID,  
         CatalogDescription.value('(/ProductDescription/@ProductName)[1]', 'varchar(40)') AS PName  
  FROM T  
GO   
```  
  
 Eseguire la query seguente sulla vista:  
  
```  
SELECT *   
FROM   MyView  
```  
  
 Risultato:  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 Tenere presente quanto segue sull'uso di `xml` tipo di dati per creare viste:  
  
-   Il tipo di dati xml può essere creato in una vista materializzata. La vista materializzata non può essere basata su un metodo con tipo di dati XML, ma è possibile eseguirne il cast su una raccolta di XML Schema diversa dalla colonna di tipo xml nella tabella di base.  
  
-   Il `xml` tipo di dati non può essere utilizzato nelle viste partizionate distribuite.  
  
-   I predicati SQL in esecuzione sulla vista non saranno inseriti in XQuery per la definizione della vista.  
  
-   I metodi con tipo di dati XML in una vista non sono aggiornabili.  
  
  
