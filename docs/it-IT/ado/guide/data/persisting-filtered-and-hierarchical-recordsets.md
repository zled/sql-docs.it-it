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
ms.openlocfilehash: 4ad6b968804bfd7dcd2b83c538ac4961c43b6aef
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Persistenza recordset filtrati e gerarchici
Se il [filtro](../../../ado/reference/ado-api/filter-property.md) è attiva per il **Recordset**, vengono salvate solo le righe accessibili in base al filtro. Se il **Recordset** è di tipo gerarchico, il membro figlio corrente **Recordset** e relativi elementi figlio viene salvati, incluso l'elemento padre **Recordset**. Se il **salvare** metodo di un elemento figlio **Recordset** viene chiamato, l'elemento figlio e i relativi elementi figlio viene salvati, ma non è l'elemento padre. Per ulteriori informazioni su gerarchica **recordset**, vedere [il Data Shaping](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Esistono alcune limitazioni quando si salva gerarchica **recordset** (forme di dati) in formato XML. Per ulteriori informazioni, vedere [salvataggio di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
