---
title: Proprietà dinamiche del recordset in formato XML | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50841931d26847ba339d64634d3eff4d7a7efc1b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712540"
---
# <a name="recordset-dynamic-properties-in-xml"></a>Proprietà dinamiche dei recordset in XML
Le seguenti proprietà specifiche del provider di Recordset (dal motore del cursore Client) vengono attualmente mantenute in formato XML:  
  
-   Update Resync  
  
-   Tabella univoca  
  
-   Schema univoco  
  
-   Catalogo univoco  
  
-   La risincronizzazione di comando  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   Proprietà dinamica Reshape Name  
  
-   AutoRecalc  
  
 Queste proprietà vengono salvate nella sezione schema come attributi di definizione dell'elemento per il Recordset vengano resi persistente. Questi attributi sono definiti nello spazio dei nomi dello schema del set di righe e deve avere il prefisso "rs:".  
  
## <a name="see-also"></a>Vedere anche  
 [Persistenza di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
