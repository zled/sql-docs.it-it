---
title: Persistenza dei recordset filtrati e gerarchici | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d7ad27e3694b7a92e560170e699f62d76d5e6b0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Persistenza recordset filtrati e gerarchici
Se il [filtro](../../../ado/reference/ado-api/filter-property.md) è attiva per il **Recordset**, vengono salvate solo le righe accessibili in base al filtro. Se il **Recordset** è di tipo gerarchico, il membro figlio corrente **Recordset** e relativi elementi figlio viene salvati, incluso l'elemento padre **Recordset**. Se il **salvare** metodo di un elemento figlio **Recordset** viene chiamato, l'elemento figlio e i relativi elementi figlio viene salvati, ma non è l'elemento padre. Per ulteriori informazioni su gerarchica **recordset**, vedere [il Data Shaping](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Esistono alcune limitazioni quando si salva gerarchica **recordset** (forme di dati) in formato XML. Per ulteriori informazioni, vedere [salvataggio di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
