---
title: Persistenza di recordset filtrati e gerarchici | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 53e28fdfbc49b53c4927bbcc0d5a6a8dc44b3d6d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811919"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Persistenza di recordset filtrati e gerarchici
Se il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà è valida per il **Recordset**, vengono salvate solo le righe accessibili in base al filtro. Se il **Recordset** è di tipo gerarchico, il membro figlio corrente **Recordset** e i relativi elementi figlio viene salvati, incluso l'elemento padre **Recordset**. Se il **salvare** metodo di un elemento figlio **Recordset** viene chiamato, l'elemento figlio e i relativi elementi figlio viene salvati, ma non è l'elemento padre. Per altre informazioni sulle gerarchica **recordset**, vedere [Data Shaping](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Si applicano alcune limitazioni quando si salva gerarchica **recordset** (forme di dati) in formato XML. Per altre informazioni, vedere [record di persistenza in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
