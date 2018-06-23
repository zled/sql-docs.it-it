---
title: MSSQLSERVER_32042 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 32042 (Database Engine error)
ms.assetid: 53a51c7a-dcd4-4c15-b4d2-6aaa9dce76da
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2dc82f65ed2044ac5edc324e78d743dd6b6e9622
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067817"
---
# <a name="mssqlserver32042"></a>MSSQLSERVER_32042
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|32042|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum32042|  
|Testo del messaggio|Generato avviso relativo a un log non inviato. Il valore corrente di '%d' è maggiore della soglia '%d'.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo evento di mirroring del database viene generato nell'istanza del server principale per indicare che la quantità di log non inviato ha raggiunto un valore soglia specificato dall'utente. In genere questo evento viene generato a causa di un cambiamento delle prestazioni del sistema. La larghezza di banda disponibile tra i due sistemi è diminuita o il carico è aumentato.  
  
 La quantità di log non inviato è una misurazione delle prestazioni che consente di valutare possibili perdite di dati in termini di numero di KB di log non inviato. Questa misurazione è particolarmente rilevante per le sessioni in modalità a prestazioni elevate. Questa misurazione è inoltre utile come sessione in modalità a sicurezza elevata quando il mirroring viene sospeso in seguito alla disconnessione dei partner.  
  
## <a name="user-action"></a>Azione dell'utente  
 Controllare il carico delle istanze del server principale e del server mirror e la connessione di rete tra i sistemi per determinare la causa del problema.  
  
## <a name="see-also"></a>Vedere anche  
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Usare valori di soglia avvisi e avvisi sulle metriche delle prestazioni di mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  