---
title: Il servizio Microsoft cursore per OLE DB | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5dd9f4b279bd38028bb529dcdd0a49f32ffd7cc7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>Il servizio Microsoft cursore per OLE DB
Quando si seleziona un cursore sul lato client o impostare il **CursorLocation** proprietà **adUseClient**, si sta chiamando il servizio di cursore per OLE DB. È possibile visualizzare i riferimenti a "Client Cursor Engine", che è sostanzialmente la stessa operazione nel contesto di ADO. Questo servizio integra le funzioni di supporto cursore dei provider di dati. Di conseguenza, che è possibile disporre di funzionalità relativamente uniforme di tutti i provider di dati.  
  
 Il servizio di cursore per OLE DB rende disponibili le proprietà dinamiche e migliora il comportamento di alcuni metodi. Ad esempio, il **Ottimizza** proprietà dinamica consente la creazione di indici temporanei per rendere alcune operazioni, ad esempio il **trovare** metodo.  
  
 Il servizio cursore consente il supporto per l'aggiornamento in batch in tutti i casi. Inoltre, simula più in grado di supportare tipi di cursore, ad esempio i cursori dinamici, quando un provider di dati possa fornire solo i cursori meno in grado di supportare, ad esempio i cursori statici.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio cursore Microsoft per OLE DB (ADO servizio componente)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
