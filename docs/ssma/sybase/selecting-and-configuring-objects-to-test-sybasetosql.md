---
title: La selezione e configurazione di oggetti a Test (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester Component,Parameter Comparision Setting
- Tester Component,Selecting Objects
ms.assetid: 89c23aad-bfee-4917-bc16-175288390ac0
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26d6e9d0a07ddc32f20c80f3d0d476131721d969
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="selecting-and-configuring-objects-to-test-sybasetosql"></a>La selezione e configurazione di oggetti a Test (SybaseToSQL)
In questo passaggio si selezionano oggetti da testare e configurare le impostazioni per il confronto dei parametri di output procedure e funzioni, nonché i valori restituiti delle funzioni.  
  
## <a name="selection-of-objects-to-test"></a>Selezione di oggetti di Test  
Nell'albero degli oggetti Sybase che si trova sul lato sinistro della finestra, controllare gli oggetti a cui che si desidera richiamare durante il processo di test. Visualizzare l'elenco completo degli oggetti testabili nel [test gli oggetti di Database migrati &#40;SybaseToSQL&#41; ](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md) argomento.  
  
Se il Tester di SSMA non supporta gli oggetti selezionati per il test, verrà visualizzato il collegamento con l'etichetta **ad alcuni oggetti selezionati contengono errori** sotto l'albero di oggetti. Fare clic su questo collegamento per visualizzare i motivi per cui questi oggetti non possono essere testati e cancellare la selezione di oggetti non corretti.  
  
Sul lato destro è possibile visualizzare più pagine di **SQL** pagina Mostra la definizione dell'oggetto corrente. Nel **precedenti SQL** e **SQL Post** pagine è possono specificare gli script da eseguire prima e dopo la chiamata di avvio di oggetto di test. Si tratta di può essere utile quando l'oggetto richiede ulteriori oggetti tali tabelle temporanee o cursori. Il **parametri** pagina sono elencati i parametri se l'oggetto è una stored procedure o una funzione. Il **proprietà** pagina Mostra le caratteristiche aggiuntive dell'oggetto. Vedere la descrizione di **parametri Comparsions** e **chiamare valori** le pagine seguenti.  
  
## <a name="parameter-comparison-settings"></a>Impostazioni di confronto dei parametri  
Stabilire le regole di confronto per i parametri di output e restituire valori di **il confronto dei parametri** pagina. È possibile apportare le seguenti impostazioni.  
  
### <a name="use-during-comparisons"></a>Utilizzo durante i confronti  
Abilitare l'utilizzo del parametro selezionato per il confronto di risultati di test.  
  
-   Se si sceglie **True**, SSMA confronterà il valore di output di questo parametro dopo avere eseguito la procedura in Sybase con il valore corrispondente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]  
  
-   Se si sceglie**False**, il parametro verrà escluso dalla verifica dei risultati.  
  
### <a name="use-custom-scale"></a>Utilizzare una scala personalizzata  
Per i parametri di tipo di dati numerico di lunghezza fissa e approssimativo, è possibile impostare una scala personalizzata per il confronto.  
  
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
È possibile specificare i valori dei parametri di input nel **chiamare valori** pagina. Il **Aggiungi chiamata** pulsante consente di aggiungere una nuova chiamata con valori di parametri vuoto. Il **rimuovere chiamare** pulsante consente di rimuovere la chiamata corrente.  
  
## <a name="next-step"></a>Passaggio successivo  
[La selezione e la configurazione di oggetti interessati &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Test di eseguire la migrazione di oggetti di Database &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
