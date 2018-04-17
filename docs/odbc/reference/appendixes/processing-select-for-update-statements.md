---
title: L'elaborazione di SELECT per le istruzioni UPDATE | Documenti Microsoft
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
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], select for update statements
- select for update [ODBC]
- SQL statements [ODBC], cursor library
- cursor library [ODBC], select for update statements
- ODBC cursor library [ODBC], select for update statements
- cursor library [ODBC], statement processing
ms.assetid: 8d2e79a4-5daf-458e-a536-d8b6e588753e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3c1af5a6c3bdd4a04f0d901158643e29d40962a6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="processing-select-for-update-statements"></a>L'elaborazione di SELECT per le istruzioni UPDATE
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 Per garantire la massima interoperabilità, applicazioni devono generare set di risultati che verrà aggiornato con un'istruzione di aggiornamento posizionato tramite l'esecuzione di un **selezionare per aggiornare** istruzione. Anche se la libreria di cursori non è richiesto, è necessaria per la maggior parte delle origini dati che supportano le istruzioni per gli aggiornamenti posizionati.  
  
 La libreria di cursori ignora le colonne di **FOR UPDATE** clausola di un **SELECT FOR UPDATE** istruzione; prima di passare l'istruzione per il driver rimuove questa clausola. Nella libreria di cursori, l'attributo di istruzione SQL_ATTR_CONCURRENCY, con le restrizioni descritti nella sezione precedente, i controlli se impostare le colonne in un risultato possono essere aggiornati.
