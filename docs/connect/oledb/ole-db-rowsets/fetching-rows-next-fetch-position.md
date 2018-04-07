---
title: Posizione del recupero successivo | Documenti Microsoft
description: Recupero righe - posizione del recupero successiva
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
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
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c5870fefce6e4d989235f5ec1d0672e4b77866d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="fetching-rows---next-fetch-position"></a>Recupero di righe - posizione del recupero successiva
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server mantiene tenere traccia della posizione del recupero successivo in modo che una sequenza di chiamate per il **GetNextRows** metodo (senza salti, modifiche di direzione o intermedi le chiamate al **FindNextRow** **Seek**, o **esecuzione di RestartPosition** metodi) legge l'intero set di righe senza ignorare o ripetizione di una riga. Posizione del recupero successivo viene modificata tramite la chiamata a **IRowset:: GetNextRows**, **IRowset:: RestartPosition**, o **IRowsetIndex:: Seek**, oppure chiamando **FindNextRow** con un valore null *pBookmark* valore. La chiamata **FindNextRow** con un valore diverso da null *pBookmark* valore non influisce sulla posizione del recupero successivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di righe](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
