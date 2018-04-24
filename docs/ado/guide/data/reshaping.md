---
title: Modificare la forma | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- reshaping previously shaped Recordset [ADO]
- data shaping [ADO], reshaping
ms.assetid: b1c965b7-3dad-4de6-9e0e-502ca8785be3
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 58a09ecb5ad1828a94bdc5e5b82e59de61396be6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="reshaping"></a>Modifica della forma
Oggetto **Recordset** creato da una clausola di una forma comando può essere assegnato un *alias* nome (in genere con la parola chiave AS). L'alias di una forma **Recordset** a cui fa riferimento in un comando completamente diverso. Ovvero, è possibile riutilizzare o *rielaborare*, una forma precedentemente **Recordset** in un nuovo comando shape. Per supportare questa funzionalità, ADO.NET fornisce una proprietà, [modificare la forma di nome](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md).  
  
 Modificare la forma ha due funzioni principali. Il primo consiste nell'associare un oggetto esistente **Recordset** con un nuovo padre **Recordset**.  
  
## <a name="example"></a>Esempio  
  
```  
rs1.Open "SHAPE {select * from Customers} " & _  
         "APPEND ({select * from Orders} AS chapOrders " & _  
         "RELATE CustomerID to CustomerID)", cn  
  
rs2.Open "SHAPE {select * from Employees} " & _  
         "APPEND (chapOrders RELATE EmployeeID to EmployeeID)", cn  
```  
  
 È la seconda funzione per abilitare l'accesso non faceva parte di un figlio esistente **Recordset** oggetti, utilizzando la sintassi "SHAPE \<recordset modificare la forma di nome >".  
  
> [!NOTE]
>  È possibile aggiungere colonne a un oggetto esistente **Recordset**, modificare la forma con un parametri **Recordset** o **Recordset** gli oggetti in una clausola COMPUTE frapposto o eseguire operazioni su una qualsiasi di aggregazione **Recordset** discendenti dal **Recordset** quest'ultimo. Il **Recordset** quest'ultimo e la nuova forma comando entrambi devono utilizzare la stessa [connessione](../../../ado/reference/ado-api/connection-object-ado.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di data shaping](../../../ado/guide/data/data-shaping-example.md)
