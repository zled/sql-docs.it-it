---
title: Miglioramento delle prestazioni e affidabilità con il Driver JDBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58521cbe6c21e7ef58fc97b52e1ef6b27209e4fe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32833146"
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>Utilizzo del driver JDBC per il miglioramento di prestazioni e affidabilità
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Uno degli aspetti dello sviluppo di applicazioni comune a tutte le applicazioni è l'esigenza costante di migliorare prestazioni e affidabilità. Esistono diverse tecniche per raggiungere questo obiettivo con il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 Negli argomenti di questa sezione vengono descritte le varie tecniche per il miglioramento di prestazioni e affidabilità quando si utilizza il driver JDBC.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Chiusura di oggetti non in uso](../../connect/jdbc/closing-objects-when-not-in-use.md)|Descrive l'importanza di chiudere gli oggetti del driver JDBC quando non sono più necessari.|  
|[Gestione delle dimensioni delle transazioni](../../connect/jdbc/managing-transaction-size.md)|Descrive le tecniche per migliorare le prestazioni delle transazioni.|  
|[Uso di istruzioni e set di risultati](../../connect/jdbc/working-with-statements-and-result-sets.md)|Descrive le tecniche per migliorare le prestazioni quando si utilizza l'istruzione o set di risultati di oggetti.|  
|[Uso del buffer adattivo](../../connect/jdbc/using-adaptive-buffering.md)|Viene descritta una caratteristica di buffer adattivo, progettata per recuperare qualsiasi tipo di dati con valori di grandi dimensioni senza l'overhead dei cursori server.|  
|[Colonne di tipo sparse](../../connect/jdbc/sparse-columns.md)|Viene descritto il supporto del driver JDBC per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] colonne di tipo sparse.|  
|[Memorizzazione nella cache dei metadati delle istruzioni preparate per JDBC Driver](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|Vengono descritte le tecniche per migliorare le prestazioni delle query di istruzione preparata.|
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  