---
title: Panoramica di dati di aggiornamento | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- updating data [ODBC], about updating data
- data updates [ODBC]
- updating data [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e5accaa3a443f7cc850fd6b4012430043d402203
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="updating-data-overview"></a>Panoramica di aggiornamento dati
Le applicazioni possono aggiornare i dati tramite l'esecuzione di istruzioni SQL o chiamando **SQLSetPos** o **SQLBulkOperations**. **AGGIORNAMENTO**, **eliminare**, e **inserire** istruzioni agire direttamente sull'origine dati e in genere sono supportate dal driver. La ricerca di aggiornamenti e le istruzioni delete contengono una specifica della riga da modificare. Aggiornamento posizionato e istruzioni delete e **SQLSetPos** agire sull'origine dati tramite un cursore e meno ampiamente supportati.  
  
 Se i cursori possono rilevare le modifiche apportate al set di risultati con i metodi descritti in questa sezione varia a seconda del tipo di cursore e modalità di implementazione. I cursori forward-only non periodiche di righe e pertanto non rileverà le modifiche. Per informazioni sulla possibilità di rilevare le modifiche cursori scorrevoli, vedere [cursori scorrevoli](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Istruzioni UPDATE, DELETE e INSERT](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Istruzioni di eliminazione e aggiornamento posizionato](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Simulazione di istruzioni di eliminazione e aggiornamento posizionato](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Determinazione del numero di righe interessate](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Aggiornamento dati con SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Aggiornamento dei dati con SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Dati di tipo Long e SQLSetPos e SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
