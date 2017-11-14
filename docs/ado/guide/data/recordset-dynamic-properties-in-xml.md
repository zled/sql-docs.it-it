---
title: "Le proprietà dinamiche dell'oggetto Recordset in XML | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 62d9b59fc1145e09f89bbe69b8d7b6e561798e70
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
 [Salvataggio di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md)

