---
title: Tipi di cursore | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5b1c041c135586d46f3a777aff411b0e1ed03258
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="cursor-types"></a>Tipi di cursore
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC definisce quattro tipi di cursore supportati da Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client. I cursori si differenziano in relazione alla capacità di rilevare le modifiche apportate al set di risultati e le risorse utilizzate, ad esempio memoria e lo spazio **tempdb**. Tramite un cursore è possibile rilevare le modifiche apportate alle righe solo quando viene eseguito un secondo tentativo di recupero di tali righe. L'origine dei dati non è in grado di notificare al cursore le eventuali modifiche apportate alle righe in fase di recupero. La capacità di rilevamento delle modifiche non effettuate di un cursore inoltre varia in base al livello di isolamento delle transazioni.  
  
 Di seguito sono indicati i quattro cursori ODBC supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   I cursori forward only non supportano lo scorrimento, ma solo le operazioni di recupero seriale delle righe dall'inizio alla fine del cursore.  
  
-   I cursori statici vengono compilati **tempdb** quando il cursore è aperto. Un cursore statico visualizza sempre il set di risultati così come è visualizzato all'apertura del cursore. Non riflettono mai modifiche ai dati. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono sempre di sola lettura. Poiché un cursore server statico viene compilato come una tabella di lavoro in **tempdb**, le dimensioni del set di risultati del cursore non possono superare le dimensioni massime consentite da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   L'appartenenza e l'ordine delle righe di un cursore gestito da keyset vengono fissati al momento dell'apertura del cursore. Eventuali modifiche alle colonne non chiave sono visibili tramite il cursore.  
  
-   I cursori dinamici sono l'opposto dei cursori statici. Essi riflettono tutte le modifiche apportate alle righe del set di risultati corrispondente. I valori di dati, l'ordine e l'appartenenza delle righe del set di risultati possono variare a ogni operazione di recupero.  
  
## <a name="see-also"></a>Vedere anche  
 [Tramite i cursori & #40; ODBC & #41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
