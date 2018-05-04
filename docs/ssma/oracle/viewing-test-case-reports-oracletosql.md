---
title: Visualizzazione dei report di Test Case (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: d5c3a5077ce213c32b3e6e49c273d6be38aac9f8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="viewing-test-case-reports-oracletosql"></a>Visualizzazione dei report di Test Case (OracleToSQL)
Il Report di Test Case Mostra i risultati della verifica di test e informazioni generali del test. In caso di errore di test, viene visualizzate anche informazioni su tutti i dati non corrispondente negli oggetti verificati.  
  
## <a name="report-structure"></a>Struttura del report  
Nella parte superiore del report visualizzato queste statistiche:  
  
-   Numero totale di oggetti testati e il numero di oggetti per cui il test completata.  
  
-   Il numero totale di verificato le tabelle e le chiavi esterne e il numero di tabelle e le chiavi esterne corrispondente correttamente.  
  
-   L'ora di inizio, ora di fine del test case e il tempo totale impiegato per l'esecuzione.  
  
Il resto del report mostra le informazioni in quattro categorie:  
  
**Errori di prerequisiti**  
Mostra gli errori che si è verificato il **passaggio prerequisiti.** In genere, viene ignorato.  
  
**Inizializzazione**  
Mostra lo stato di esecuzione come **successo** o **errore**.  
  
**Gli oggetti risultato del test**  
Confronto dei risultati (esito positivo o negativo) e le mancate corrispondenze che il Tester di SSMA rilevato in caso di errore.  
  
**Finalizzazione**  
Mostra lo stato di esecuzione come **successo** o **errore**.  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di Test case &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test di eseguire la migrazione di oggetti di Database &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
