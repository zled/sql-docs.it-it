---
title: Spostare elementi in una soluzione | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- moving items
- solutions [SQL Server Management Studio], item relocation
- relocating items
ms.assetid: b40a24eb-f528-4e70-b26e-5eaf6e0ed1ed
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b6393b571e0458d64ff16952268eeda8e8a2ae5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="move-items-in-a-solution"></a>Spostare elementi in una soluzione
Gli elementi nei progetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] sono query, connessioni e file esterni. In Esplora soluzioni è possibile spostare query e file esterni tra progetti, mentre le connessioni non possono essere spostate.  
  
### <a name="to-move-items-in-solution-explorer"></a>Per spostare elementi in Esplora soluzioni  
  
1.  In Esplora soluzioni selezionare l'elemento che si desidera spostare.  
  
2.  Scegliere **Taglia** dal menu **Modifica**.  
  
3.  Sempre in Esplora soluzioni selezionare la destinazione.  
  
4.  Scegliere **Incolla** dal menu **Modifica**.  
  
È possibile spostare elementi trascinando query e file esterni in Esplora soluzioni e visualizzare il risultato dell'operazione di trascinamento. Se si spostano query da un tipo di progetto a un altro, è possibile che tali query vengano considerate file esterni nel progetto di destinazione.  
  
> [!NOTE]  
> Quando si sposta una query connessa, la connessione al progetto di destinazione non viene spostata, quindi la query perderà la connessione dopo essere stata spostata nel progetto di destinazione.  
  
## <a name="see-also"></a>Vedere anche  
[Esplora soluzioni](../../ssms/solution/solution-explorer.md)  
[Copia di elementi in una soluzione](../../ssms/solution/copy-items-in-a-solution.md)  
  
