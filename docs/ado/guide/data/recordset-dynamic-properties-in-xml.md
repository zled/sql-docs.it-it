---
title: Le proprietà dinamiche dell'oggetto Recordset in XML | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd874d0db6d026b82ddbc8055a17a073194c6e07
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272330"
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
