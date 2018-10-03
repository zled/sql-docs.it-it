---
title: Posizione del recupero successivo | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c47f1a8692cf7d2e3fb4f00c64770b3b0c69e5a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087232"
---
# <a name="next-fetch-position"></a>Posizione del recupero successivo
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Native Client provider tiene traccia della posizione del recupero successivo in modo che una sequenza di chiamate per il **GetNextRows** metodo (senza salti, modifiche di direzione o intermedi le chiamate al  **FindNextRow**, **Seek**, o **esecuzione di RestartPosition** metodi) legge l'intero set di righe senza ignorare o ripetere una riga. La posizione del recupero successiva viene modificata chiamando **IRowset::GetNextRows**, **IRowset::RestartPosition** o **IRowsetIndex::Seek** oppure chiamando **FindNextRow** con un valore *pBookmark* Null. La chiamata a **FindNextRow** con un valore *pBookmark* non Null non influisce sulla posizione del recupero successivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di righe](fetching-rows.md)  
  
  
