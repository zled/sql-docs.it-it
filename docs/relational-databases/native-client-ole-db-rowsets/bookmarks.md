---
title: I segnalibri | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4e2d096056d8477481c0a06420db4006abb12fad
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bookmarks"></a>Segnalibri
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  I segnalibri consentono ai consumer di tornare rapidamente su una riga. Grazie ai segnalibri, essi possono accedere in modo casuale alle righe in base al valore del segnalibro. La colonna del segnalibro è la colonna 0 nel set di righe. Il consumer imposta il valore del campo dwFlag della struttura di associazione su DBCOLUMNSINFO_ISBOOKMARK per indicare che la colonna viene utilizzata come segnalibro. Imposta inoltre la proprietà del set di righe DBPROP_BOOKMARKS su VARIANT_TRUE, consentendo alla colonna 0 di essere presente nel set di righe. Il **IRowsetLocate:: GetRowsAt** metodo viene quindi utilizzato per recuperare le righe a partire dalla riga specificata come un offset da un segnalibro.  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
