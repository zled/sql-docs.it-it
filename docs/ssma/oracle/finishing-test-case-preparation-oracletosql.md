---
title: Completamento della preparazione del Test Case (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32f38713-7ae4-48d3-980d-74cadc8545a0
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: f6bf969705a049e03212500a3112e643fbe7654a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="finishing-test-case-preparation-oracletosql"></a>Completamento della preparazione del Test Case (OracleToSQL)
Pagina finale della procedura guidata consente di visualizzare la descrizione di Test Case e informazioni sugli oggetti coinvolti nel test. Inoltre, in questa pagina è possibile impostare il test di opzioni di esecuzione.  
  
Il **informazioni di Test Case** sezione mostra il nome del Test Case e la descrizione.  
  
Il **gli oggetti selezionati per essere testati** sezione contiene l'elenco di oggetti testati raggruppati per tipo di oggetto denominato.  
  
Il **oggetti interessati da Test che verranno analizzati** sezione consente di visualizzare l'elenco di oggetti quali le modifiche dei dati devono essere confrontate dopo l'esecuzione di oggetti testati denominato.  
  
## <a name="test-case-settings"></a>Impostazioni di test Case  
Nel **le impostazioni di Test Case** sezione è possibile impostare le opzioni di test l'esecuzione seguente:  
  
### <a name="stop-test-execution-after-first-failure"></a>Arrestare l'esecuzione di test dopo il primo errore  
Specifica per interrompere il test se si verifica un errore durante l'esecuzione di test.  
  
-   Se si sceglie **Sì**, verificare l'esecuzione di interrompe se si verifica un errore.  
  
-   Se si sceglie **n**, l'esecuzione dei test continua dopo un errore.  
  
### <a name="perform-data-rollback"></a>Eseguire il rollback di dati  
Consente di eseguire il rollback automatico dei dati dopo l'esecuzione di test.  
  
-   Se si sceglie **Sì**, le modifiche ai dati andranno perduti dopo l'esecuzione dei test.  
  
-   Se si sceglie **n**, tutti i test verranno salvate le modifiche ai dati di esecuzione.  
  
### <a name="auxiliary-tables-saving-mode"></a>Modalità di salvataggio di tabelle ausiliarie  
Definisce la modalità di salvataggio delle tabelle ausiliarie creato durante l'esecuzione di test. Vedere la descrizione delle tabelle ausiliarie il [OracleToSQL esegue Test case &#40; &#41;](../../ssma/oracle/running-test-cases-oracletosql.md) argomento.  
  
-   Se si seleziona **Salva sempre**, dati di tabelle ausiliari verranno sempre archiviati per un uso successivo.  
  
-   Se si seleziona **se il confronto tra le tabelle non è stato possibile salvare**, verranno archiviati i dati di tabelle ausiliari solo se si verifica un errore.  
  
-   Se si seleziona **Elimina sempre**, tabelle ausiliarie sempre eliminati dopo l'esecuzione dei test.  
  
-   Se si seleziona **utente chiedere se non è riuscita confronto tra le tabelle**, l'utente può selezionare le azioni necessarie se si verifica un errore.  
  
Fare clic su di **fine** pulsante per salvare il Test Case preparata in [utilizzando Test repository (OracleToSQL)](http://msdn.microsoft.com/en-us/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4).  
  
## <a name="see-also"></a>Vedere anche  
[Tramite il repository Test &#40; OracleToSQL &#41;](../../ssma/oracle/using-test-repositories-oracletosql.md)  
[Esecuzione di Test case &#40; OracleToSQL &#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test di eseguire la migrazione di oggetti di Database &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
