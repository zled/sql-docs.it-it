---
title: Scrittura di un'applicazione interoperabile | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: 8b42b8ae-7862-4b63-a0b3-2a204e0c43a5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6aae50c316072c0970ffea4eb953f4e0ee86c5d5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="writing-an-interoperable-application"></a>Scrittura di un'applicazione di interoperabilità
Ogni volta che un'applicazione utilizza lo stesso codice con più di un driver, il codice deve essere interoperabile tra i driver. Nella maggior parte dei casi, si tratta di un'attività semplice. Ad esempio, il codice per recuperare le righe con un cursore forward-only è uguale per tutti i driver. In alcuni casi, può essere più difficile. Ad esempio, il codice per costruire gli identificatori per l'utilizzo nelle istruzioni SQL deve considerare il caso di identificatore, racchiudere tra virgolette e convenzioni di denominazione in tre parti, due parti e una parte.  
  
 In generale, codice di interoperabilità deve affrontano problemi di supporto delle funzionalità e la variabilità delle funzionalità. *Supporto alle funzionalità* fa riferimento a o meno una particolare caratteristica è supportata. Ad esempio, non tutti i DBMS supportano le transazioni e interoperativa codice deve funzionare correttamente indipendentemente dal supporto delle transazioni. *Funzionalità variabilità* fa riferimento a variazione nel modo in cui è supportata una determinata funzionalità. Ad esempio, i nomi di catalogo si trovano all'inizio degli identificatori di alcuni DBMS e alla fine di identificatori in altri.  
  
 È possono gestire le applicazioni con supporto di funzionalità e la variabilità delle funzionalità in fase di progettazione o in fase di esecuzione. Per risolvere il supporto delle funzionalità e la variabilità in fase di progettazione, uno sviluppatore esamina il DBMS di destinazione e i driver e assicura che lo stesso codice saranno interoperabile tra di essi. Si tratta in genere il modo in cui le applicazioni con bassa o limitate interoperabilità gestiscono questi problemi.  
  
 Ad esempio, se lo sviluppatore garantisce che un'applicazione verticale funziona solo con quattro DBMS particolare e ognuno di tali DBMS supporta le transazioni, l'applicazione non è necessario codice per verificare il supporto delle transazioni in fase di esecuzione. È possibile presupporre sempre le transazioni sono disponibili a causa delle decisioni in fase di progettazione da usare solo quattro DBMS, ognuno dei quali supporta le transazioni.  
  
 Per risolvere il supporto delle funzionalità e la variabilità in fase di esecuzione, l'applicazione deve testare per diverse funzionalità in fase di esecuzione e agire di conseguenza. Si tratta in genere il modo in cui le applicazioni altamente interoperabile gestiscono questi problemi. Per i problemi di supporto di funzionalità, ciò significa la scrittura di codice che rende il codice facoltativo o la scrittura di funzionalità che emula la funzionalità quando non è disponibile. Per problemi di funzionalità variabilità, ciò significa la scrittura di codice che supporta tutte le possibili varianti.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Controllo del supporto e della variabilità delle funzionalità](../../../odbc/reference/develop-app/checking-feature-support-and-variability.md)  
  
-   [Funzionalità da controllare](../../../odbc/reference/develop-app/features-to-watch-for.md)
