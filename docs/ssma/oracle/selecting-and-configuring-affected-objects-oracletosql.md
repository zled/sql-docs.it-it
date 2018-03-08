---
title: Selezione e configurazione interessati oggetti (OracleToSQL) | Documenti Microsoft
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
helpviewer_keywords:
- Columns Comparison Settings
- Selection of Affected Objects
ms.assetid: 545eeda2-9829-4187-a858-619a96b4b71d
caps.latest.revision: "8"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 1a4fe479f53c914b4417cd0069335fa8bb0da027
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="selecting-and-configuring-affected-objects-oracletosql"></a>Selezione e configurazione interessato (OracleToSQL) di oggetti
In questa pagina è possibile selezionare tabelle e le chiavi esterne, le modifiche in cui devono essere confrontate quando SSMA verifica i risultati dell'esecuzione per gli oggetti scelto nel passaggio precedente. Inoltre, è possibile personalizzare i parametri di verifica.  
  
## <a name="selection-of-affected-objects"></a>Selezione degli oggetti interessati  
Nell'albero degli oggetti Oracle si trova sul lato sinistro della finestra, selezionare le tabelle e le chiavi esterne, le modifiche in cui devono essere confrontate per identica.  
  
Se il Tester di SSMA non può verificare uno di questi oggetti, verrà visualizzato il collegamento con l'etichetta **ad alcuni oggetti selezionati contengono errori** sotto l'albero di oggetti. Fare clic su questo collegamento per visualizzare i motivi per cui non è possibile confrontare questi oggetti e per cancellare la selezione di oggetti non corretti.  
  
## <a name="table"></a>Tabella  
Scheda della tabella contiene la visualizzazione della griglia della tabella selezionata. La griglia include le informazioni seguenti relative alla tabella selezionata:  
  
-   Nome colonna  
  
-   Tipo di dati  
  
-   Precisione  
  
-   Scala  
  
-   Regola  
  
-   Default  
  
-   Identity  
  
-   Ammette valori Null  
  
## <a name="sql"></a>Sql  
Scheda SQL contiene "Create table" SQL della tabella selezionata.  
  
## <a name="data"></a>data  
Scheda dati Visualizza i dati presenti nella tabella selezionata.  
  
## <a name="properties"></a>Proprietà  
Scheda proprietà Visualizza le proprietà della tabella selezionata. I campi seguenti sono presenti nella scheda proprietà:  
  
-   Creazione o dell'ultima modifica  
  
-   Nome oggetto  
  
## <a name="columns-comparison-settings"></a>Impostazioni di confronto di colonne  
Stabilire le regole di confronto per le colonne della tabella in **confronto delle colonne** pagina. È possibile apportare le seguenti impostazioni.  
  
### <a name="use-during-test-comparisons"></a>Utilizzo durante i confronti tra Test  
Determinare se la colonna partecipa alla verifica dei risultati del test.  
  
-   Se si sceglie **True**, SSMA confronterà il contenuto della colonna dopo l'esecuzione del test in Oracle con il contenuto della colonna in SQL Server. 
  
-   Se si sceglie**False**, la colonna verrà escluso dalla verifica dei risultati.  
  
### <a name="use-custom-scale"></a>Utilizzare una scala personalizzata  
Per le colonne di tipo di dati numerici, è possibile impostare una scala personalizzata per il confronto.  
  
-   Se si sceglie **True**, valori numerici saranno arrotondati in base al **confronto scala** valore prima che vengano confrontati.  
  
-   Se si sceglie**False**, il confronto numerico sarà esatto.  
  
### <a name="comparing-scale"></a>Il confronto di scala  
  
-   Disponibile solo se il **scala personalizzata utilizzare** opzione è impostata su **True**. Questa è la precisione per un confronto numerico.  
  
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
  
-   Se si sceglie **False**, il confronto verrà tenuto in considerazione maiuscole e minuscole.  
  
## <a name="comparing-sql"></a>Il confronto di SQL  
È possibile visualizzare le istruzioni SELECT generate da Tester SSMA nel **confronto SQL** pagina. Il Tester confronterà i set di risultati di queste istruzioni in base a una riga per riga. Ogni riga successiva di un set di risultati Oracle deve essere uguale alla riga successiva del set di risultati prodotto in SQL Server.
  
È possibile modificare le istruzioni SELECT per fornire una verifica personalizzata. Per salvare le modifiche in Oracle e nelle istruzioni SQL Server, utilizzare il **applica** pulsanti sotto l'origine e destinazione SQL, in modo analogo.  
  
## <a name="next-step"></a>Passaggio successivo  
[Personalizzazione dell'ordine delle chiamate &#40; OracleToSQL &#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Completamento della preparazione del Test Case &#40; OracleToSQL &#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
[Esecuzione di Test case &#40; OracleToSQL &#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test di eseguire la migrazione di oggetti di Database &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
