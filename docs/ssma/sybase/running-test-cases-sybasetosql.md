---
title: Esecuzione di Test case (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester Component,Execution Steps
ms.assetid: 195ffdef-cfde-4bf4-a3ae-e7402bb07972
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 5751a704fdea6e7c87aa43e1b4fedc1107d89f8c
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779357"
---
# <a name="running-test-cases-sybasetosql"></a>Esecuzione di Test case (SybaseToSQL)
Quando SSMA Tester esegue un Test Case, esegue gli oggetti selezionati per il test e crea un report sui risultati della verifica. Se i risultati sono identici in entrambe le piattaforme, il test completata. La corrispondenza degli oggetti tra Sybase e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] viene determinato in base alle impostazioni di mapping dello schema per il progetto SSMA corrente.  
  
Un requisito necessario per un test riuscito è che tutti gli oggetti di Sybase vengono convertiti e caricati nel database di destinazione. Inoltre, i dati della tabella devono essere migrati in modo che il contenuto delle tabelle in entrambe le piattaforme è sincronizzato.  
  
## <a name="run-test-case"></a>Eseguire Test Case  
Per eseguire i Test Case preparata:  
  
1.  Fare clic su di **eseguire** pulsante.  
  
2.  Nel **Connetti Sybase** nella finestra di dialogo immettere le informazioni di connessione e quindi fare clic su **Connetti**.  
  
Una volta completato il test, viene creato il Report di Test Case. Fare clic sui **rapporto** pulsante per visualizzare il [visualizzazione di report di Test Case &#40;SybaseToSQL&#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md). Il risultato del test (rapporto Test Case) viene automaticamente archiviato nel [repository Test utilizzando &#40;SybaseToSQL&#41; ](../../ssma/sybase/using-test-repositories-sybasetosql.md) per un uso successivo.  
  
## <a name="test-case-execution-steps"></a>Passaggi per l'esecuzione dei test Case  
  
### <a name="prerequisites"></a>Prerequisiti  
SSMA Tester controlla se vengono soddisfatti tutti i prerequisiti per l'esecuzione di test prima dell'inizio del test. Se alcune condizioni non vengono soddisfatti, viene visualizzato un messaggio di errore.  
  
### <a name="initialization"></a>Inizializzazione  
In questo passaggio, SSMA Tester crea ausiliari oggetti (tabelle, trigger e viste) sia di Sybase e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Consentono di modifiche apportate nelle tabelle interessate scelte per la verifica se la modalità tabella confronti traccia **cambia solo**.  
  
Si supponga che la tabella verificata viene denominata USER_TABLE. Per una tabella, vengono creati i seguenti oggetti ausiliari in Sybase.  
  
I seguenti oggetti vengono creati Sybase in database SSMATESTER2005db o SSMATESTER2008db e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nel database ssmatesterdb_syb.  
  
|nome|Tipo|Description|  
|--------|--------|---------------|  
|USER_TABLE$Trg|Trigger|Controllo delle modifiche nella tabella verificata di trigger.|  
|USER_TABLE$Aud|Tabella|Tabella in cui vengono salvate le righe eliminate o sovrascritte.|  
|USER_TABLE$AudID|Tabella|Tabella in cui vengono salvate le righe nuove e modificate.|  
|USER_TABLE|Vista|Rappresentazione semplificata delle modifiche nella tabella.|  
|USER_TABLE$new|Vista|Rappresentazione semplificata di righe inserite e sovrascritte.|  
|USER_TABLE$new_id|Vista|Identificazione di righe inserite e modificate.|  
|USER_TABLE$old|Vista|Rappresentazione semplificata di righe eliminate o sovrascritte.|  
  
L'oggetto seguente viene creato nel database della tabella verificato Sybase e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
|nome|Tipo|Description|  
|--------|--------|---------------|  
|USER_TABLE$Trg|Trigger|Controllo delle modifiche nella tabella verificata di trigger.|  
  
### <a name="test-object-calls"></a>Chiamate di oggetti di test  
In questo passaggio, il Tester di SSMA richiama ogni oggetto selezionato per il test, vengono confrontati i risultati e viene mostrato il report.  
  
### <a name="finalization"></a>Finalizzazione  
Durante la finalizzazione SSMA Tester pulisce gli oggetti ausiliari, creati nel **inizializzazione** passaggio.  
  
## <a name="next-step"></a>Passaggio successivo  
[Visualizzazione dei report di Test Case &#40;SybaseToSQL&#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[La selezione e configurazione di oggetti di Test &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md)  
[La selezione e la configurazione di oggetti interessati &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
[Test di eseguire la migrazione di oggetti di Database &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
