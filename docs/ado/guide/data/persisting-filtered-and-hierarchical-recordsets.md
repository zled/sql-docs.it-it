---
title: Persistenza dei recordset filtrati e gerarchici | Documenti Microsoft
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
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d945999ef7feb34ebe7de3b945868bc35c154589
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Persistenza recordset filtrati e gerarchici
Se il [filtro](../../../ado/reference/ado-api/filter-property.md) è attiva per il **Recordset**, vengono salvate solo le righe accessibili in base al filtro. Se il **Recordset** è di tipo gerarchico, il membro figlio corrente **Recordset** e relativi elementi figlio viene salvati, incluso l'elemento padre **Recordset**. Se il **salvare** metodo di un elemento figlio **Recordset** viene chiamato, l'elemento figlio e i relativi elementi figlio viene salvati, ma non è l'elemento padre. Per ulteriori informazioni su gerarchica **recordset**, vedere [il Data Shaping](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Esistono alcune limitazioni quando si salva gerarchica **recordset** (forme di dati) in formato XML. Per ulteriori informazioni, vedere [salvataggio di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
