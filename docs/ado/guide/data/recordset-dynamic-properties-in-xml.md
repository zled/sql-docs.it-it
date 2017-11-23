---
title: "Le proprietà dinamiche dell'oggetto Recordset in XML | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
caps.latest.revision: "3"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 925981765184f05deadfda8ca8b27a929a6387ab
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="recordset-dynamic-properties-in-xml"></a>Proprietà dinamiche dell'oggetto Recordset in XML
Attualmente, le seguenti proprietà specifiche del provider di Recordset (da Client Cursor Engine) vengono mantenute nel formato XML:  
  
-   Risincronizzazione di aggiornamento  
  
-   Tabella univoca  
  
-   Schema univoco  
  
-   Catalogo univoca  
  
-   Risincronizzazione di comando  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   Modificare la forma di nome  
  
-   AutoRecalc  
  
 Queste proprietà vengono salvate nella sezione schema come attributi della definizione dell'elemento per il Recordset permanente. Questi attributi sono definiti nello spazio dei nomi dello schema del set di righe e deve avere il prefisso "rs:".  
  
## <a name="see-also"></a>Vedere anche  
 [Persistenza di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
