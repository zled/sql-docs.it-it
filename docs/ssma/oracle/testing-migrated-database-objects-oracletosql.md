---
title: Test di eseguire la migrazione di oggetti di Database (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f03ef5e1-66e6-4c84-ada2-252dd5ada82f
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 3b908317227b497911084e4c5de1c27ccb8361d1
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34778017"
---
# <a name="testing-migrated-database-objects-oracletosql"></a>Test di eseguire la migrazione di oggetti di Database (OracleToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per Oracle Tester (SSMA Tester) verifica automaticamente la conversione di oggetti di database e la migrazione dei dati apportate da SSMA. Al termine di tutti i passaggi di migrazione di SSMA, è possibile utilizzare il Tester di SSMA per verificare che gli oggetti convertiti funzionano nello stesso modo e che tutti i dati è stato trasferito correttamente.  
  
È possibile verificare i seguenti tipi di oggetto con SSMA Tester:  
  
-   Tabelle  
  
-   Stored procedure, incluse quelle nel pacchetto.  
  
-   Funzioni definite dall'utente, incluse le funzioni nel pacchetto.  
  
-   Visualizzazioni.  
  
-   Istruzioni autonome.  
  
SSMA Tester esegue gli oggetti selezionati per il testing in Oracle e le relative controparti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Successivamente, confronta i risultati in base ai criteri seguenti:  
  
-   Le modifiche nei dati di tabella sono identiche?  
  
-   I valori dei parametri di output per le procedure e funzioni identiche?  
  
-   Le funzioni restituiscono gli stessi risultati?  
  
-   Sono che i set di risultati identici?  
  
> [!NOTE]  
> Attenzione. Non utilizzare mai SSMA Tester nei sistemi di produzione. Durante l'esecuzione di Tester lo schema di origine e i dati vengono modificati. Nel frattempo, il ripristino completo dello stato originale potrebbe essere impossibile per alcuni tipi di codice testato.  
  
## <a name="prerequisites"></a>Prerequisiti  
Se si desidera utilizzare SSMA Tester, installare SSMA Oracle estensione con la **installare Database Tester** opzione attivata.  
  
Per consentire il confronto dei dati della tabella risultante, impostare il **colonna ROWID generare** opzione **Sì** prima che venga avviata la conversione dello schema. SSMA verrà aggiunta una colonna ROWID a tutte le tabelle durante l'esecuzione del **convertire Schema** comando.  
  
Inoltre, verificare quanto segue:  
  
-   Vengono installati gli strumenti client Oracle nel computer in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] viene eseguito.  
  
-   Integrazione con Common Language Runtime (CLR) è stato attivato il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] motore di Database.  
  
Si noti che la versione corrente di SSMA Tester non supporta l'esecuzione parallela da utenti diversi nello stesso server di origine o di destinazione.  
  
## <a name="getting-started"></a>Introduzione  
[Creazione di Test case &#40;OracleToSQL&#41;](../../ssma/oracle/creating-test-cases-oracletosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Installazione dei componenti di SSMA in SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Le impostazioni del progetto &#40;conversione&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  
