---
title: Tipi di cursore scorrevole | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: dbd32576-0453-4e90-ae45-1a81cee8259d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 989f573a68fb818ca7f09d90ae0160d65e7a39c1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="scrollable-cursor-types"></a>Tipi di cursore scorrevole
I quattro tipi di cursori scorrevoli sono statici, dinamici, basati su keyset e misto. I cursori statici rilevano poche o nessuna modifica, ma sono relativamente economici da implementare. I cursori dinamici rilevano tutte le modifiche, ma sono costosi da implementare. I cursori keyset e misti si trovano rilevano la maggior parte delle modifiche, ma meno spese rispetto ai cursori dinamici.  
  
 I termini seguenti vengono utilizzati per definire le caratteristiche di ogni tipo di cursore scorrevole:  
  
-   **Il proprietario degli aggiornamenti, eliminazioni e inserimenti.** Gli aggiornamenti, eliminazioni e inserimenti eseguiti nel cursore, con una chiamata a **SQLBulkOperations** o **SQLSetPos** o con un oggetto posizionato istruzioni update o delete.  
  
-   **Altri aggiornamenti, si elimina e si inserisce.** Gli aggiornamenti, eliminazioni e inserimenti non effettuati dal cursore, incluse quelle apportate da altre operazioni nella stessa transazione, quelle apportate tramite altre transazioni e quelle apportate da altre applicazioni.  
  
-   **Appartenenza al gruppo.** Il set di righe nel set di risultati.  
  
-   **Ordine.** L'ordine in cui vengono restituite le righe dal cursore.  
  
-   **I valori.** I valori in ogni riga nel set di risultati.  
  
 Per informazioni su come aggiornare, eliminare e inserire i dati, vedere [Panoramica di aggiornamento dati](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Cursori statici ODBC](../../../odbc/reference/develop-app/odbc-static-cursors.md)  
  
-   [Cursori dinamici ODBC](../../../odbc/reference/develop-app/odbc-dynamic-cursors.md)  
  
-   [Cursori gestiti da keyset](../../../odbc/reference/develop-app/keyset-driven-cursors.md)  
  
-   [Cursori misti](../../../odbc/reference/develop-app/mixed-cursors.md)
