---
title: I cursori dinamici | Documenti Microsoft
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
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab212d978f38a9e80435d0fae81a6664a8839b56
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270410"
---
# <a name="dynamic-cursors"></a>Cursori dinamici
I cursori dinamici rilevano tutte le modifiche apportate alle righe nel set di risultati, indipendentemente dal fatto che si verificano le modifiche dall'interno del cursore o da altri utenti all'esterno del cursore. Tutti i insert, update e le istruzioni delete eseguite da tutti gli utenti sono visibili tramite il cursore. Cursore dinamico può rilevare eventuali modifiche apportate alle righe, ordine e i valori nel set di risultati dopo l'apertura del cursore. Gli aggiornamenti eseguiti all'esterno del cursore non sono visibili finché vengono eseguite (a meno che il livello di isolamento delle transazioni è impostato su "commit").  
  
 Si supponga, ad esempio, un cursore dinamico recuperi due righe e un'altra applicazione, quindi aggiorna una di queste righe e consente di eliminare l'altro. Se il cursore dinamico quindi recupera tali righe, non troverà la riga eliminata, ma verrà visualizzati i nuovi valori per la riga aggiornata.  
  
 Cursore dinamico è una scelta ottimale se l'applicazione deve rilevare tutti gli aggiornamenti simultanei apportati da altri utenti. Utilizzare il **Impostare CursorTypeEnum** per indicare che si desidera utilizzare un cursore dinamico in ADO.  
  
## <a name="see-also"></a>Vedere anche  
 [Cursori forward-Only](../../../ado/guide/data/forward-only-cursors.md)   
 [Cursori statici](../../../ado/guide/data/static-cursors.md)   
 [Cursori keyset](../../../ado/guide/data/keyset-cursors.md)
