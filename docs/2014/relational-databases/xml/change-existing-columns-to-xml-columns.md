---
title: Convertire colonne esistenti in colonne XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- tables [XML]
ms.assetid: 0d951424-9862-41fe-bd46-127f1c059bcb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ff63ea72b88658d9504030612f77bb948e7462ed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48226521"
---
# <a name="change-existing-columns-to-xml-columns"></a>Conversione di colonne esistenti a colonne XML
  L'istruzione ALTER TABLE supporta il `xml` tipo di dati. Ad esempio, è possibile modificare qualsiasi colonna di tipo stringa il `xml` tipo di dati. Si noti che in questi casi è necessaria la correttezza del formato dei documenti contenuti nella colonna. Se inoltre si sta modificando il tipo della colonna da stringa a XML tipizzato, i documenti nella colonna vengono convalidati rispetto agli schemi XSD specificati.  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 nvarchar(max))  
GO  
INSERT INTO T   
VALUES (1, '<Root><Product ProductID="1"/></Root>')  
GO  
ALTER TABLE T   
ALTER COLUMN Col2 xml  
GO  
```  
  
 È possibile modificare una colonna di tipo `xml` da XML non tipizzato a XML tipizzato. Esempio:  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T   
values (1, '<p1:ProductDescription ProductModelID="1"   
xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
            </p1:ProductDescription>')  
GO   
-- Make it a typed xml column by specifying a schema collection.  
ALTER TABLE T   
ALTER COLUMN Col2 xml (Production.ProductDescriptionSchemaCollection)  
GO  
```  
  
> [!NOTE]  
>  Lo script verrà eseguito sul database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , poiché la raccolta XML Schema `Production.ProductDescriptionSchemaCollection`viene creata come parte del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
 Nell'esempio precedente, tutte le istanze archiviate nella colonna vengono convalidate e tipizzate rispetto agli schemi XSD nella raccolta specificata. Se la colonna contiene una o più istanze XML non valide rispetto allo schema specificato, l'istruzione `ALTER TABLE` avrà esito negativo e non sarà possibile modificare il tipo della colonna da XML non tipizzato a XML tipizzato.  
  
> [!NOTE]  
>  Se una tabella è di grandi dimensioni, modifica un `xml` colonna di tipo può essere costoso. poiché è necessario un controllo di correttezza del formato di ogni documento e, nel caso del codice XML tipizzato, è necessaria anche la convalida.  
  
 Per altre informazioni sul codice XML tipizzato, vedere [Confrontare dati XML tipizzati con dati XML non tipizzati](compare-typed-xml-to-untyped-xml.md).  
  
  
