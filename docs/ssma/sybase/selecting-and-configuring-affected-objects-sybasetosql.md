---
title: Selezione e configurazione interessati oggetti (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester Component,Affected Objects
ms.assetid: a219df74-543a-4aec-aeeb-79f90ac3e2ee
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8e5f4fcb5af81da2b78520542e2b57bd66bc4fd1
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="selecting-and-configuring-affected-objects-sybasetosql"></a>Selezione e configurazione interessato (SybaseToSQL) di oggetti
In questa pagina è possibile selezionare tabelle e le chiavi esterne, le modifiche in cui devono essere confrontate quando SSMA verifica i risultati dell'esecuzione per gli oggetti scelto nel passaggio precedente. Inoltre, è possibile personalizzare i parametri di verifica.  
  
## <a name="selection-of-affected-objects"></a>Selezione degli oggetti interessati  
Nell'albero degli oggetti Sybase si trova sul lato sinistro della finestra, selezionare le tabelle e le chiavi esterne, le modifiche in cui devono essere confrontate per identica.  
  
Se il Tester di SSMA non può verificare uno di questi oggetti, verrà visualizzato il collegamento con l'etichetta **ad alcuni oggetti selezionati contengono errori** sotto l'albero di oggetti. Fare clic su questo collegamento per visualizzare i motivi per cui non è possibile confrontare questi oggetti e per cancellare la selezione di oggetti non corretti.  
  
## <a name="table"></a>Tabella  
Scheda della tabella contiene la visualizzazione della griglia della tabella selezionata. La griglia include le informazioni seguenti relative alla tabella selezionata:  
  
-   Nome colonna  
  
-   Tipo di dati  
  
-   Precisione  
  
-   Scala  
  
-   Rule  
  
-   Valore predefinito  
  
-   Identity  
  
-   Ammette valori Null  
  
## <a name="sql"></a>Sql  
Scheda SQL contiene "Create table" SQL della tabella selezionata.  
  
## <a name="data"></a>Dati  
Scheda dati Visualizza i dati presenti nella tabella selezionata.  
  
## <a name="properties"></a>Proprietà  
Scheda proprietà Visualizza le proprietà della tabella selezionata. I campi seguenti sono presenti nella scheda proprietà:  
  
-   Creazione o dell'ultima modifica  
  
-   Nome oggetto  
  
## <a name="table-comparison-settings"></a>Impostazioni di confronto di tabella  
Stabilire le regole di confronto per la tabella in **confronti di tabelle** pagina. È possibile apportare le seguenti impostazioni.  
  
### <a name="comparison-mode"></a>Modalità di confronto  
Definisce il contenuto della tabella in cui verrà eseguito il confronto.  
  
-   Se si seleziona **solo modifiche**, verrà eseguito un confronto completo di righe della tabella.  
  
-   Se si seleziona **completo**, verrà eseguito il confronto solo per le righe che sono state modificate.  
  
## <a name="column-comparison-settings"></a>Impostazioni di confronto delle colonne  
Stabilire le regole di confronto per le colonne della tabella in **colonna confronti** pagina. È possibile apportare le seguenti impostazioni.  
  
### <a name="use-during-test-comparisons"></a>Utilizzo durante i confronti tra Test  
Determinare se la colonna partecipa alla verifica dei risultati del test.  
  
-   Se si sceglie **True**, SSMA confronterà il contenuto della colonna dopo l'esecuzione del test in Sybase con il contenuto della colonna in SQL Server.
  
-   Se si sceglie **False**, la colonna verrà escluso dalla verifica dei risultati.  
  
### <a name="use-custom-scale"></a>Utilizzare una scala personalizzata  
Per le colonne di tipo di dati numerici, è possibile impostare una scala personalizzata per il confronto.  
  
-   Se si sceglie **True**, valori numerici saranno arrotondati in base al **confronto scala** valore prima che vengano confrontati.  
  
-   Se si sceglie **False**, il confronto numerico sarà esatto.  
  
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
È possibile visualizzare le istruzioni SELECT generate da Tester SSMA nel **confrontare SQL** pagina. Il Tester confronterà i set di risultati di queste istruzioni in base a una riga per riga. Ogni riga successiva di un set di risultati Sybase deve essere uguale alla riga successiva del set di risultati restituito in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
È possibile modificare le istruzioni SELECT per fornire una verifica personalizzata. Per salvare le modifiche in Sybase e in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istruzioni, utilizzare il **applica** pulsanti sotto l'origine e destinazione SQL, in modo analogo.  
  
## <a name="next-step"></a>Passaggio successivo  
[Personalizzazione dell'ordine delle chiamate &#40; SybaseToSQL &#41;](../../ssma/sybase/customizing-calls-order-sybasetosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di Test case &#40; SybaseToSQL &#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Test di eseguire la migrazione di oggetti di Database &#40; SybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  

