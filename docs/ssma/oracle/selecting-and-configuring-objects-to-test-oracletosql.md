---
title: La selezione e configurazione di oggetti a Test (OracleToSQL) | Documenti Microsoft
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
- Selection of Objects to Test,Parameter Comparison Settings
ms.assetid: 29fb6542-5c1f-4b14-a822-87700beb7623
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3b12a1b9ec20f736072d57039d247be13be57e69
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="selecting-and-configuring-objects-to-test-oracletosql"></a>La selezione e configurazione di oggetti a Test (OracleToSQL)
In questo passaggio si selezionano oggetti da testare e configurare le impostazioni per il confronto dei parametri di output procedure e funzioni, nonché i valori restituiti delle funzioni.  
  
## <a name="selection-of-objects-to-test"></a>Selezione di oggetti di Test  
Nell'albero degli oggetti Oracle che si trova sul lato sinistro della finestra, controllare gli oggetti a cui che si desidera richiamare durante il processo di test. Visualizzare l'elenco completo degli oggetti testabili nel [OracleToSQL test gli oggetti di Database migrati &#40; &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md) argomento.  
  
Se il Tester di SSMA non supporta gli oggetti selezionati per il test, verrà visualizzato il collegamento con l'etichetta **ad alcuni oggetti selezionati contengono errori** sotto l'albero di oggetti. Fare clic su questo collegamento per visualizzare i motivi per cui questi oggetti non possono essere testati e cancellare la selezione di oggetti non corretti.  
  
Sul lato destro è possibile visualizzare più pagine di **SQL** pagina Mostra la definizione dell'oggetto corrente. Il **parametri** pagina sono elencati i parametri se l'oggetto è una stored procedure o una funzione. Il **proprietà** pagina Mostra le caratteristiche aggiuntive dell'oggetto. Vedere la descrizione di **parametro confronti** e **chiamare valori** le pagine seguenti.  
  
## <a name="parameter-comparison-settings"></a>Impostazioni di confronto dei parametri  
Stabilire le regole di confronto per i parametri di output e restituire valori nel **parametro confronti** pagina. È possibile apportare le seguenti impostazioni.  
  
### <a name="use-during-test-comparisons"></a>Utilizzo durante i confronti tra Test  
Abilitare l'utilizzo del parametro selezionato per il confronto di risultati di test.  
  
-   Se si sceglie **True**, SSMA confronterà il valore di output di questo parametro dopo avere eseguito la procedura in Oracle con il valore corrispondente in SQL Server.
  
-   Se si sceglie**False**, il parametro verrà escluso dalla verifica dei risultati.  
  
### <a name="use-custom-scale"></a>Utilizzare una scala personalizzata  
Per i parametri di tipo di dati numerici, è possibile impostare una scala personalizzata per il confronto.  
  
-   Se si sceglie **True**, valori numerici saranno arrotondati in base al **confronto scala** valore prima che vengano confrontati.  
  
-   Se si sceglie**False**, il confronto numerico sarà esatto.  
  
### <a name="comparing-scale"></a>Il confronto di scala  
Disponibile solo se il **scala personalizzata utilizzare** opzione è impostata su **True**. Questa è la precisione per un confronto numerico.  
  
### <a name="date-time-comparing"></a>Confronto tra ora data  
Definisce la data e ora vengono confrontati i valori.  
  
-   Se si seleziona **confrontare intero data**, verrà eseguito un confronto completo di valori di entrambe le piattaforme.  
  
-   Se si seleziona **confrontare solo data**, l'ora parte verrà ignorata.  
  
-   Se si seleziona **confrontare solo ora**, la data parte verrà ignorata.  
  
-   Se si seleziona **millisecondi ignorare**, verranno confrontati i risultati fino a secondi.  
  
-   Se si seleziona **data ignorare e millisecondi**, il risultato sarà ignorate e confrontati solo da parte dell'ora frazione di secondo.  
  
### <a name="ignore-strings-case"></a>Ignora maiuscole/minuscole di stringhe  
Controlla la distinzione maiuscole/minuscole del confronto.  
  
-   Se si sceglie **True**, il confronto verrà fatta distinzione tra maiuscole e minuscole.  
  
-   Se si sceglie **False**, il confronto sarà tra maiuscole e minuscole.  
  
### <a name="ignore-trailing-spaces"></a>Ignora spazi finali  
Controlla come spazi vengono considerati durante il confronto.  
  
-   Se si sceglie **True**, le stringhe confrontate saranno tagliati a destra prima il confronto.  
  
-   Se si sceglie **False**, le stringhe confrontate conserverà gli spazi finali.  
  
## <a name="specify-input-values-for-procedures-and-functions-call-values"></a>Specificare i valori di input per le procedure e funzioni (chiamare valori)  
È possibile specificare i valori dei parametri di input nel **chiamare valori** pagina. Il **Aggiungi chiamata** pulsante consente di aggiungere una nuova chiamata con valori di parametri vuoto. Il **rimuovere chiamate** pulsante consente di rimuovere la chiamata corrente.  
  
## <a name="next-step"></a>Passaggio successivo  
[Selezione e configurazione interessati OracleToSQL oggetti &#40; &#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Test di eseguire la migrazione di oggetti di Database &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  

