---
title: Tramite il repository Test (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords: Tester Component,Test Repositories
ms.assetid: c359c25c-db2a-4a20-afa9-62d87a62df72
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7fc0391764e4accadb6c333cd554b9ad11a2d806
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="using-test-repositories-sybasetosql"></a>Tramite il repository Test (SybaseToSQL)
Il Repository Test SSMA archivi SSMA Tester test case e i risultati del test per un uso successivo. I dati del Repository vengono salvati nelle tabelle di SQL Server **TestCaseRepository** e **RunTestCaseResultRepository** nello schema **ssma_sybase_utilities** di **ssmatesterdb_syb** database.  
  
I pulsanti seguenti sono disponibili nella finestra di dialogo Repository del Test case:  
  
-   Fare clic su di **aggiornamento** pulsante per aggiornare l'elenco di Test case o i risultati dei Test.  
  
-   Fare clic su di **chiudere** per chiudere la finestra di dialogo di Repository del Test case.  
  
## <a name="test-cases-repository"></a>Repository di test case  
È possibile visualizzare il Repository Test case, fare clic su **Test case...** dal **Tester** menu. SSMA consente quindi di visualizzare il **Repository del Test case** finestra di dialogo con un elenco di salvato test case il **Test case** pagina.  
  
Nella griglia vengono visualizzate le informazioni seguenti relative a ogni test case:  
  
-   Nome: Il nome del test case.  
  
-   Create: Il test case data di creazione.  
  
-   Modificato: Il test case data dell'ultima modifica.  
  
-   Descrizione: Il test case descrizioni.  
  
I pulsanti seguenti sono disponibili nella pagina di Test case:  
  
-   Fare clic su di **Aggiungi** per eseguire la procedura guidata di Test Case e creare un nuovo test.  
  
-   Fare clic su di **rimuovere** pulsante per eliminare il test selezionato dal repository. Quando un Test Case viene eliminato, vengono eliminati anche tutti i risultati dei Test correlati.  
  
-   Fare clic su di **modifica** pulsante per eseguire la procedura guidata di Test Case e modificare il test selezionato.  
  
-   Fare clic su di **eseguire** pulsante per aprire la [esegue Test case &#40; SybaseToSQL &#41; ](../../ssma/sybase/running-test-cases-sybasetosql.md) finestra di dialogo ed eseguire il test selezionato.  
  
## <a name="test-results-repository"></a>Repository dei risultati del test  
È possibile visualizzare il Repository dei risultati del Test sul **risultati dei Test** pagina del **Repository del Test case** finestra. Aprirlo facendo **risultati dei Test...** dal **Tester** menu.  
  
È possibile utilizzare due filtri su **risultati dei Test** pagina:  
  
-   Il filtro del nome del Test Case: consente di scegliere i risultati dei test dal nome del test case. Questo filtro **tutti i Test Case** valore consente di visualizzare i risultati dei test per tutti i test case.  
  
-   Il filtro data di esecuzione di Test Case: filtri i risultati dei test per la data di salvataggio. Questo filtro **periodo tutti** valore consente la visualizzazione di risultati dei test per una data di salvataggio.  
  
Le seguenti informazioni sui risultati dei test viene visualizzate nella griglia.  
  
-   Nome: nome di Test case.  
  
-   Avviato: Eseguire il Test case data di esecuzione.  
  
-   : Un breve riepilogo dei risultati Dell'esecuzione del test (descrizione della cella Visualizza un riepilogo dell'esecuzione del test completo).  
  
I pulsanti seguenti sono disponibili nella pagina dei risultati di Test:  
  
-   Fare clic su di **vista** pulsante per aprire [visualizzazione di report di Test Case &#40; SybaseToSQL &#41; ](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md) del risultato del Test Case corrente.  
  
-   Fare clic su di **eliminare** pulsante per eliminare il risultato del Test selezionato  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di Test case &#40; SybaseToSQL &#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Test di eseguire la migrazione di oggetti di Database &#40; SybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
