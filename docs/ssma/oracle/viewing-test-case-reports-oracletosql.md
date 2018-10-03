---
title: Visualizzazione dei report di Test Case (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: ce59e126ce24e30e091b4a5456d8b78c84355e88
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47641769"
---
# <a name="viewing-test-case-reports-oracletosql"></a>Visualizzazione di report dei test case (OracleToSQL)
Il Report di Test Case Mostra i risultati della verifica di test e informazioni generali del test. In caso di errore di test, viene visualizzate anche informazioni su tutti i dati non corrispondenti negli oggetti di verifica.  
  
## <a name="report-structure"></a>Struttura del report  
Nella parte superiore del report visualizzato queste statistiche:  
  
-   Numero totale di oggetti testati e il numero di oggetti per il quale il test ha avuto esito positivo.  
  
-   Il numero totale di tabelle di verifica e le chiavi esterne e il numero di tabelle e le chiavi esterne corrispondente correttamente.  
  
-   L'ora di inizio, ora di fine del test case e il tempo totale impiegato per l'esecuzione.  
  
Il resto del report mostra le informazioni in quattro categorie:  
  
**Errori dei prerequisiti**  
Mostra gli errori che si è verificato il **passaggio dei prerequisiti.** In genere, viene ignorato.  
  
**Inizializzazione**  
Mostra lo stato di esecuzione **Success** oppure **errore**.  
  
**Gli oggetti risultato del test**  
Confronto dei risultati (esito positivo o negativo) e le mancate corrispondenze tra Tester SSMA rilevati in caso di errore.  
  
**Finalizzazione**  
Mostra lo stato di esecuzione **Success** oppure **errore**.  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di Test case &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test di oggetti di Database migrati &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
