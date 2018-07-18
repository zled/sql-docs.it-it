---
title: 'Esempio: specifica delle direttive ID e IDREFS | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- IDREFS directive
- ID directive
ms.assetid: 99b9f0d8-ecbb-4225-859f-881066c09785
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5483235964a1b10decad823313e3657809a7d34a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33013818"
---
# <a name="example-specifying-the-id-and-idrefs-directives"></a>Esempio: specifica delle direttive ID, IDREFS
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Un attributo dell'elemento può essere specificato come attributo di tipo **ID** e l'attributo **IDREFS** può quindi essere utilizzato per fare riferimento a tale attributo. In questo modo è possibile creare collegamenti tra più documenti, in modo analogo alla relazione esistente tra chiave primaria e chiave esterna nei database relazionali.  
  
 Nell'esempio seguente viene illustrato l'utilizzo delle direttive **ID** e **IDREFS** per la creazione di attributi dei tipi **ID** e **IDREFS** . Poiché gli ID non possono essere valori Integer, nell'esempio i valori di ID vengono convertiti, ovvero ne viene eseguito il cast di tipo. Vengono utilizzati prefissi per i valori degli ID.  
  
 Si supponga di voler generare codice XML come illustrato di seguito:  
  
```  
<Customer CustomerID="C1" SalesOrderIDList=" O11 O22 O33..." >  
    <SalesOrder SalesOrderID="O11" OrderDate="..." />  
    <SalesOrder SalesOrderID="O22" OrderDate="..." />  
    <SalesOrder SalesOrderID="O33" OrderDate="..." />  
    ...  
</Customer>  
```  
  
 L'attributo `SalesOrderIDList` dell'elemento < `Customer` > è un attributo multivalore che fa riferimento all'attributo `SalesOrderID` dell'elemento < `SalesOrder` >. Per stabilire il collegamento, è necessario dichiarare l'attributo `SalesOrderID` con il tipo di dati `ID` e l'attributo `SalesOrderIDList` dell'elemento < `Customer`> con il tipo di dati `IDREFS`. Poiché un cliente può inviare più ordini, viene utilizzato il tipo `IDREFS`.  
  
 Anche gli attributi **IDREFS** hanno più di un valore. È pertanto necessario utilizzare una clausola SELECT separata che riutilizzerà le stesse informazioni di Tag, Parent e colonna chiave. È poi necessario usare `ORDER BY` per garantire che le sequenze di righe che compongono i valori **IDREFS** vengano visualizzate raggruppate sotto il rispettivo elemento padre.  
  
 Di seguito è riportata la query che genera il codice XML desiderato. La query utilizza le direttive `ID` e `IDREFS` per sovrascrivere i tipi nei nomi di colonna (`SalesOrder!2!SalesOrderID!ID`, `Customer!1!SalesOrderIDList!IDREFS`).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID       [Customer!1!CustomerID],  
        NULL               [Customer!1!SalesOrderIDList!IDREFS],  
        NULL               [SalesOrder!2!SalesOrderID!ID],  
        NULL               [SalesOrder!2!OrderDate]  
FROM   Sales.Customer C   
UNION ALL   
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID,  
        'O-'+CAST(SalesOrderID as varchar(10)),   
        NULL,  
        NULL  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
        C.CustomerID,  
        NULL,  
        'O-'+CAST(SalesOrderID as varchar(10)),  
        OrderDate  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerIDORDER BY [Customer!1!CustomerID] ,  
         [SalesOrder!2!SalesOrderID!ID],  
         [Customer!1!SalesOrderIDList!IDREFS]  
FOR XML EXPLICIT;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo della modalità EXPLICIT con FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
