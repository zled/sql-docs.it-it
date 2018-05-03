---
title: I segnalibri | Documenti Microsoft
description: Segnalibri in OLE DB Driver per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- OLE DB Driver for SQL Server, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 26dfd57a44b11b3ca2dd748680c73f692308e05a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="bookmarks"></a>Segnalibri
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  I segnalibri consentono ai consumer di tornare rapidamente su una riga. Grazie ai segnalibri, essi possono accedere in modo casuale alle righe in base al valore del segnalibro. La colonna del segnalibro è la colonna 0 nel set di righe. Il consumer imposta il valore del campo dwFlag della struttura di associazione su DBCOLUMNSINFO_ISBOOKMARK per indicare che la colonna viene utilizzata come segnalibro. Imposta inoltre la proprietà del set di righe DBPROP_BOOKMARKS su VARIANT_TRUE, consentendo alla colonna 0 di essere presente nel set di righe. Il **IRowsetLocate:: GetRowsAt** metodo viene quindi utilizzato per recuperare le righe a partire dalla riga specificata come un offset da un segnalibro.  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
