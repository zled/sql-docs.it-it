---
title: Uso di repository Test (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Test Repositories
ms.assetid: c359c25c-db2a-4a20-afa9-62d87a62df72
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: fc4d537901d0352725260fadf1cb4446cb764419
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731119"
---
# <a name="using-test-repositories-sybasetosql"></a>Uso di repository test (SybaseToSQL)
Gli archivi di Repository Test SSMA SSMA Tester test case e risultati dei test per un uso successivo. I dati del Repository vengono salvati nelle tabelle di SQL Server **TestCaseRepository** e **RunTestCaseResultRepository** nello schema **ssma_sybase_utilities** del **ssmatesterdb_syb** database.  
  
I pulsanti seguenti sono disponibili nella finestra di dialogo del Repository del Test case:  
  
-   Scegliere il **Aggiorna** pulsante per aggiornare l'elenco di Test case o i risultati dei Test.  
  
-   Scegliere il **chiudere** per chiudere la finestra di dialogo del Repository del Test case.  
  
## <a name="test-cases-repository"></a>Repository di test case  
È possibile visualizzare il Repository di Test case facendo **Test case...** dal **Tester** menu. SSMA consente quindi di visualizzare il **Repository del Test case** finestra di dialogo con un elenco dei case di test salvati sulle **Test case** pagina.  
  
Nella griglia vengono visualizzate le informazioni seguenti su ogni test case:  
  
-   Nome: Nome del test case.  
  
-   Create: Il test case data di creazione.  
  
-   Modificato: Il test case data dell'ultima modifica.  
  
-   Descrizione: Il test case descrizioni.  
  
I pulsanti seguenti sono disponibili nella pagina di Test case:  
  
-   Scegliere il **Add** pulsante per eseguire la procedura guidata di Test Case e creare un nuovo test.  
  
-   Scegliere il **rimuovere** pulsante per eliminare il test selezionato dal repository. Quando un Test Case viene eliminato, vengono eliminati anche tutti i risultati dei Test correlati.  
  
-   Scegliere il **modifica** pulsante per eseguire la procedura guidata di Test Case e modificare il test selezionato.  
  
-   Fare clic sui **eseguiti** pulsante per aprire il [che esegue Test case &#40;SybaseToSQL&#41; ](../../ssma/sybase/running-test-cases-sybasetosql.md) finestra di dialogo ed eseguire il test selezionato.  
  
## <a name="test-results-repository"></a>Repository dei risultati del test  
È possibile visualizzare il Repository dei risultati del Test nella **i risultati del Test** pagina della **Repository del Test case** finestra. Aprirlo facendo **i risultati dei Test...** dal **Tester** menu.  
  
È possibile usare due filtri sul **i risultati dei Test** pagina:  
  
-   Il filtro del nome del Test Case: consente di scegliere i risultati dei test dal nome del test case. Questo filtro **tutti i Test Case** valore consente di visualizzare i risultati dei test per tutti i test case.  
  
-   Il filtro data di esecuzione di Test Case: risultati dei test di filtri per la data di salvataggio. Questo filtro **periodo tutti** valore consente di visualizzare i risultati dei test per una data di salvataggio.  
  
Le informazioni seguenti sui risultati dei test viene visualizzate nella griglia.  
  
-   Nome: nome di Test case.  
  
-   Avviato: Test Data del caso di esecuzione.  
  
-   Risultato: Una breve descrizione dell'esecuzione del test (descrizione comando della cella, questo visualizza un riepilogo completo dell'esecuzione del test).  
  
I pulsanti seguenti sono disponibili nella pagina dei risultati dei Test:  
  
-   Fare clic sui **View** per aprire [visualizzazione di report di Test Case &#40;SybaseToSQL&#41; ](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md) del risultato del Test Case corrente.  
  
-   Scegliere il **eliminare** pulsante per eliminare il risultato del Test selezionato  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di Test case &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Test di oggetti di Database migrati &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
