---
title: "Aggiunta di più campi | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], adding multiple fields
- editing data [ADO], AddNew method
ms.assetid: f3648ef4-9f36-4991-a868-83a617389844
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61f6d3c21d4260126f67511c31bbcc680a2da6fa
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="adding-multiple-fields-and-values"></a>Aggiunta di più campi e valori
In alcuni casi, potrebbe essere più efficiente passare una matrice di campi e i relativi valori per il **AddNew** metodo, piuttosto che impostare **valore** più volte per ogni nuovo campo. Se *elenco campi* è una matrice, *valori* deve essere una matrice con lo stesso numero di membri in caso contrario, si verifica un errore. L'ordine dei nomi di campo deve corrispondere all'ordine dei valori di campo in ogni matrice. Il codice seguente passa una matrice di campi e una matrice di valori per il **AddNew** metodo.

```
'BeginAddNew2
    Dim avarFldNames As Variant
    Dim avarFldValues As Variant

    avarFldNames = Array("CompanyName", "Phone")
    avarFldValues = Array("Sample Shipper 2", "(931) 555-6334")

    If objRs1.Supports(adAddNew) Then
        objRs1.AddNew avarFldNames, avarFldValues
    End If

    'Re-establish a Connection and update
    Set objRs1.ActiveConnection = GetNewConnection
    objRs1.UpdateBatch
'EndAddNew2
```

