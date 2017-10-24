---
title: Persistenza dei recordset filtrati e gerarchici | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8de12620e57fe9cf7235c2a1f5a1442b429197d0
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Persistenza recordset filtrati e gerarchici
Se il [filtro](../../../ado/reference/ado-api/filter-property.md) è attiva per il **Recordset**, vengono salvate solo le righe accessibili in base al filtro. Se il **Recordset** è di tipo gerarchico, il membro figlio corrente **Recordset** e relativi elementi figlio viene salvati, incluso l'elemento padre **Recordset**. Se il **salvare** metodo di un elemento figlio **Recordset** viene chiamato, l'elemento figlio e i relativi elementi figlio viene salvati, ma non è l'elemento padre. Per ulteriori informazioni su gerarchica **recordset**, vedere [il Data Shaping](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Esistono alcune limitazioni quando si salva gerarchica **recordset** (forme di dati) in formato XML. Per ulteriori informazioni, vedere [salvataggio di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md).

