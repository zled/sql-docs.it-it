---
title: Rimuovere le parentesi quadre dall'output JSON con l'opzione WITHOUT_ARRAY_WRAPPER | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WITHOUT_ARRAY_WRAPPER
ms.assetid: aa86c2d1-458e-465f-abfa-75470137d054
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 36e612b6c3759d968687d8ba35286c399de02a74
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="remove-square-brackets-from-json---withoutarraywrapper-option"></a>Rimuovere le parentesi quadre dall'output JSON con l'opzione WITHOUT_ARRAY_WRAPPER
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Per rimuovere le parentesi quadre che racchiudono l'output JSON della clausola **FOR JSON** per impostazione predefinita, specificare l'opzione **WITHOUT_ARRAY_WRAPPER** . Utilizzare questa opzione con un risultato a riga singola per generare un singolo oggetto JSON come output invece di una matrice con un solo elemento.

Se si utilizza questa opzione con un risultato di più righe, l'output risultante non è un oggetto JSON valido a causa di più elementi e le parentesi quadre mancante.  
  
## <a name="example-single-row-result"></a>Esempio (risultati a riga singola)  
L'esempio seguente mostra l'output della clausola **FOR JSON** con e senza l'opzione **WITHOUT_ARRAY_WRAPPER** .  
  
 **Query**  
  
```sql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  

 **Risultato ** con l'opzione **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{
    "year": 2015,
    "month": 12,
    "day": 15
} 
```  
  
 **Risultato** (predefinito), senza il **WITHOUT_ARRAY_WRAPPER** opzione  
  
```json  
[{
    "year": 2015,
    "month": 12,
    "day": 15
}]
```  

## <a name="example-multiple-row-result"></a>Esempio (risultato più righe)
Ecco un altro esempio di clausola **FOR JSON** con e senza l'opzione **WITHOUT_ARRAY_WRAPPER** . In questo esempio produce un risultato di più righe. L'output non è un oggetto JSON valido a causa di più elementi e le parentesi quadre mancante.
  
 **Query**  
  
```sql  
SELECT TOP 3 SalesOrderNumber, OrderDate, Status  
FROM Sales.SalesOrderHeader  
ORDER BY ModifiedDate  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  
  
 **Risultato ** con l'opzione **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
} 
```  
  
 **Risultato** (predefinito), senza il **WITHOUT_ARRAY_WRAPPER** opzione  
  
```json  
[{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}]
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Acquisire familiarità con il supporto JSON integrato in SQL Server  
Per un numero elevato di soluzioni specifiche, casi di utilizzo e indicazioni, vedere il [post di blog sul supporto JSON predefinito](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e Database SQL di Azure per Microsoft Program Manager Jovan Popovic.
  
## <a name="see-also"></a>Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  

