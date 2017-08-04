---
title: Tramite il repository Test (OracleToSQL) | Documenti Microsoft
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
- Test Cases Repository
- Test Results Repository
ms.assetid: f941cce4-d3e3-4aeb-a88a-4f101a97a9f4
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c3d2c6665c6d1852b291e69d2494343b5000ac06
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="using-test-repositories-oracletosql"></a>Tramite il repository Test (OracleToSQL)
Il Repository Test SSMA archivi SSMA Tester test case e i risultati del test per un uso successivo. I dati del Repository vengono salvati nelle tabelle di SQL Server **TestCaseRepository** e **RunTestCaseResultRepository** nello schema **ssma_oracle_utilities** di **ssmatesterdb** database.  
  
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
  
-   Fare clic su di **eseguire** pulsante per aprire la [esegue Test case (OracleToSQL)](http://msdn.microsoft.com/en-us/fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02) finestra di dialogo ed eseguire il test selezionato.  
  
## <a name="test-results-repository"></a>Repository dei risultati del test  
È possibile visualizzare il Repository dei risultati del Test sul **risultati dei Test** pagina del **Repository del Test case** finestra. Aprirlo facendo **risultati dei Test...** dal **Tester** menu.  
  
È possibile utilizzare due filtri su **risultati dei Test** pagina:  
  
-   Il filtro del nome del Test Case: consente di scegliere i risultati dei test dal nome del test case. Questo filtro **tutti i Test case** valore consente di visualizzare i risultati dei test per tutti i test case.  
  
-   Il filtro data di esecuzione di Test Case: filtri i risultati dei test per la data di salvataggio. Questo filtro **periodo tutti** valore consente la visualizzazione di risultati dei test per una data di salvataggio.  
  
Le seguenti informazioni sui risultati dei test viene visualizzate nella griglia.  
  
-   Nome: nome di Test case.  
  
-   Salvato: Test case data di salvataggio.  
  
-   : Un breve riepilogo dei risultati Dell'esecuzione del test (descrizione della cella Visualizza un riepilogo dell'esecuzione del test completo).  
  
I pulsanti seguenti sono disponibili nella pagina dei risultati di Test:  
  
-   Fare clic su di **vista** pulsante per aprire [OracleToSQL visualizzazione di report di Test Case &#40; &#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md) del risultato del Test Case corrente.  
  
-   Fare clic su di **eliminare** pulsante per eliminare il risultato del Test selezionato  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di Test case &#40; OracleToSQL &#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test di eseguire la migrazione di oggetti di Database &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  

