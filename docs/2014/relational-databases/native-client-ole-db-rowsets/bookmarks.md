---
title: I segnalibri | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6bc03a966ecd3d467f66d41f5ba8318b47b95f71
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170119"
---
# <a name="bookmarks"></a>Segnalibri
  I segnalibri consentono ai consumer di tornare rapidamente su una riga. Grazie ai segnalibri, essi possono accedere in modo casuale alle righe in base al valore del segnalibro. La colonna del segnalibro è la colonna 0 nel set di righe. Il consumer imposta il valore del campo dwFlag della struttura di associazione su DBCOLUMNSINFO_ISBOOKMARK per indicare che la colonna viene utilizzata come segnalibro. Imposta inoltre la proprietà del set di righe DBPROP_BOOKMARKS su VARIANT_TRUE, consentendo alla colonna 0 di essere presente nel set di righe. Il **IRowsetLocate:: GetRowsAt** metodo viene quindi utilizzato per recuperare righe a partire dalla riga specificata come un offset da un segnalibro.  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](rowsets.md)  
  
  