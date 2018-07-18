---
title: Posizione del recupero successivo | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d6fa0247cafa0d0750f224e3b369965fd4e7989
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423570"
---
# <a name="next-fetch-position"></a>Posizione del recupero successivo
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Native Client provider tiene traccia della posizione del recupero successivo in modo che una sequenza di chiamate per il **GetNextRows** metodo (senza salti, modifiche di direzione o intermedi le chiamate al  **FindNextRow**, **Seek**, o **esecuzione di RestartPosition** metodi) legge l'intero set di righe senza ignorare o ripetere una riga. Posizione del recupero successivo viene modificata chiamando **IRowset:: GetNextRows**, **IRowset:: RestartPosition**, o **IRowsetIndex:: Seek**, oppure chiamando **FindNextRow** con un valore null *pBookmark* valore. La chiamata **FindNextRow** con un valore diverso da null *pBookmark* valore non influisce sulla posizione del recupero successivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di righe](fetching-rows.md)  
  
  
