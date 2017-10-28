---
title: Creazione di Test case (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Test Case Wizard
ms.assetid: 22f38901-ec35-4707-a911-784e6ad8dafb
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c40ee9da718fec017381740d69b6fa71045572bd
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="creating-test-cases-oracletosql"></a>Creazione di Test case (OracleToSQL)
Utilizzare la procedura guidata di Test Case per creare un test. Questa procedura guidata consente di creare test case scegliendo testato e verificato gli oggetti e specificando i parametri di test.  
  
## <a name="starting-the-test-case-wizard"></a>Avvio della procedura guidata di Test Case  
Per avviare Creazione guidata Test Case **nuovo Test Case...** dal **Tester** menu.  
  
All'avvio, la procedura guidata cerca schema SSMATESTER_ORACLE sul server Oracle di origine. È lo schema di estensione Tester utilizzato per archiviare gli oggetti ausiliari. Se la procedura guidata di Test Case non è possibile trovare SSMATESTER_ORACLE, verrà visualizzata una finestra di dialogo che si propone di creare lo schema. (Questa situazione si verifica in genere durante la prima esecuzione di SSMA Tester)  
  
Se si ottiene la finestra di dialogo, fare clic su **Sì** creare schema SSMATESTER_ORACLE nel server di origine. Si noti che è necessario disporre dei privilegi di Oracle per creare un nuovo utente e gli oggetti nello schema di questo utente.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Panoramica della creazione di Test case usando la procedura guidata  
Il processo di creazione di un test case è costituita da cinque passaggi:  
  
1.  [Inizializzazione OracleToSQL Test case &#40; &#41;](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [Selezione e configurazione di oggetti per Test &#40; OracleToSQL &#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [Selezione e configurazione interessati OracleToSQL oggetti &#40; &#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [Personalizzazione dell'ordine delle chiamate &#40; OracleToSQL &#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [Completamento della preparazione del Test Case &#40; OracleToSQL &#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Test di eseguire la migrazione di oggetti di Database &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  

