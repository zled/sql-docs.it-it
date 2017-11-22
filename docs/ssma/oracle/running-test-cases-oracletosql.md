---
title: Esecuzione di Test case (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: ff5baf3dadeee06d33f5d75f0c62a1ee339ba2b3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="running-test-cases-oracletosql"></a>Esecuzione di Test case (OracleToSQL)
Quando SSMA Tester esegue un Test Case, esegue gli oggetti selezionati per il test e crea un report sui risultati della verifica. Se i risultati sono identici in entrambe le piattaforme, il test completata. La corrispondenza degli oggetti tra Oracle e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] viene determinato in base alle impostazioni di mapping dello schema per il progetto SSMA corrente.  
  
Un requisito necessario per un test riuscito è che tutti gli oggetti Oracle vengono convertiti e caricati nel database di destinazione. Inoltre, i dati della tabella devono essere migrati in modo che il contenuto delle tabelle in entrambe le piattaforme è sincronizzato.  
  
## <a name="run-test-case"></a>Eseguire Test Case  
Per eseguire i Test Case preparata:  
  
1.  Fare clic su di **eseguire** pulsante.  
  
2.  Nel **Connect to Oracle** nella finestra di dialogo immettere le informazioni di connessione e quindi fare clic su **Connetti**.  
  
Una volta completato il test, viene creato il Report di Test Case. Fare clic su di **Report** pulsante per visualizzare il [Report di Test Case](http://msdn.microsoft.com/en-us/8da14323-9dd6-4019-bf79-3e8b972a9bc0). Il risultato del test (rapporto Test Case) viene automaticamente archiviato nel [Repository dei risultati Test](http://msdn.microsoft.com/en-us/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4) per un uso successivo.  
  
## <a name="test-case-execution-steps"></a>Passaggi per l'esecuzione dei test Case  
  
### <a name="prerequisites"></a>Prerequisiti  
SSMA Tester controlla se vengono soddisfatti tutti i prerequisiti per l'esecuzione di test prima dell'inizio del test. Se alcune condizioni non vengono soddisfatti, viene visualizzato un messaggio di errore.  
  
### <a name="initialization"></a>Inizializzazione  
In questo passaggio, il Tester di SSMA crea oggetti ausiliari (tabelle, trigger e viste) nello schema SSMATESTER_ORACLE del server Oracle. Consentono apportate alla traccia degli oggetti interessati scelto per la verifica.  
  
Si supponga che la tabella verificata viene denominata USER_TABLE. Per una tabella, vengono creati i seguenti oggetti ausiliari in Oracle.  
  
||||  
|-|-|-|  
|Nome|Tipo|Description|  
|Trg $ USER_TABLE|trigger|Controllo delle modifiche nella tabella verificata di trigger.|  
|USER_TABLE$ AUD|table|Tabella in cui vengono salvate le righe eliminate o sovrascritte.|  
|USER_TABLE$ AUDID|table|Tabella in cui vengono salvate le righe nuove e modificate.|  
|USER_TABLE|vista|Rappresentazione semplificata delle modifiche nella tabella.|  
|$ USER_TABLE NEW|vista|Rappresentazione semplificata di righe inserite e sovrascritte.|  
|USER_TABLE$ NEW_ID|vista|Identificazione di righe inserite e modificate.|  
|$ USER_TABLE PRECEDENTE|vista|Rappresentazione semplificata di righe eliminate o sovrascritte.|  
  
L'oggetto seguente viene creato nello schema della tabella verificato [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
||||  
|-|-|-|  
|Nome|Tipo|Description|  
|Trg $ USER_TABLE|trigger|Controllo delle modifiche nella tabella verificata di trigger.|  
  
E vengono creati gli oggetti seguenti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]nel database ssmatesterdb.  
  
||||  
|-|-|-|  
|Nome|Tipo|Description|  
|USER_TABLE$ Aud|table|Tabella in cui vengono salvate le righe eliminate o sovrascritte.|  
|USER_TABLE$ AudID|table|Tabella in cui vengono salvate le righe nuove e modificate.|  
|USER_TABLE|vista|Rappresentazione semplificata delle modifiche nella tabella.|  
|$ USER_TABLE nuovo|vista|Rappresentazione semplificata di righe inserite e sovrascritte.|  
|USER_TABLE$ new_id|vista|Identificazione di righe inserite e modificate.|  
|$ USER_TABLE precedente|vista|Rappresentazione semplificata di righe eliminate o sovrascritte.|  
  
### <a name="test-object-calls"></a>Chiamate di oggetti di test  
In questo passaggio, il Tester di SSMA richiama ogni oggetto selezionato per il test, vengono confrontati i risultati e viene mostrato il report.  
  
### <a name="finalization"></a>Finalizzazione  
Durante la finalizzazione SSMA Tester pulisce gli oggetti ausiliari, creati nel **inizializzazione** passaggio.  
  
## <a name="next-step"></a>Passaggio successivo  
[Visualizzazione di report di Test Case &#40; OracleToSQL &#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Selezione e configurazione di oggetti per Test &#40; OracleToSQL &#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
[Selezione e configurazione interessati OracleToSQL oggetti &#40; &#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
[Test di eseguire la migrazione di oggetti di Database &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
