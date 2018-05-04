---
title: Completamento della preparazione del Test Case (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester Component,Test Case Settings
ms.assetid: 8b2a49b0-4296-4f3f-9e56-323aa6a6fa8e
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: cf1519483abcf25493e036bc524c6fdc9a1e919e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="finishing-test-case-preparation-sybasetosql"></a>Completamento della preparazione del Test Case (SybaseToSQL)
Pagina finale della procedura guidata consente di visualizzare la descrizione di Test Case e informazioni sugli oggetti coinvolti nel test. Inoltre, in questa pagina è possibile impostare il test di opzioni di esecuzione.  
  
Il **informazioni di Test Case** sezione mostra il nome del Test Case e la descrizione.  
  
Il **oggetti Test** sezione contiene l'elenco di oggetti testati raggruppati per tipo di oggetto denominato.  
  
Il **oggetti interessati da analizzare** sezione consente di visualizzare l'elenco di oggetti quali le modifiche dei dati devono essere confrontate dopo l'esecuzione di oggetti testati denominato.  
  
## <a name="test-case-settings"></a>Impostazioni di test Case  
Nel **le impostazioni di Test Case** sezione è possibile impostare le opzioni di test l'esecuzione seguente:  
  
### <a name="stop-test-execution-after-first-failure"></a>Arrestare l'esecuzione di test dopo il primo errore  
Specifica per interrompere il test se si verifica un errore durante l'esecuzione di test.  
  
-   Se si sceglie **Sì**, verificare l'esecuzione di interrompe se si verifica un errore.  
  
-   Se si sceglie **n**, l'esecuzione dei test continua dopo un errore.  
  
### <a name="perform-data-rollback"></a>Eseguire il rollback di dati  
Abilitare il rollback automatico dei dati dopo l'esecuzione di test.  
  
-   Se si sceglie **Sì**, le modifiche ai dati andranno perduti dopo l'esecuzione dei test.  
  
-   Se si sceglie **n**, tutti i test verranno salvate le modifiche ai dati di esecuzione.  
  
### <a name="auxiliary-tables-saving-mode"></a>Modalità di salvataggio di tabelle ausiliarie  
Definisce la modalità di salvataggio delle tabelle ausiliarie creato durante l'esecuzione di test. Vedere la descrizione delle tabelle ausiliarie il [che esegue Test case &#40;SybaseToSQL&#41; ](../../ssma/sybase/running-test-cases-sybasetosql.md) argomento.  
  
-   Se si seleziona **Salva sempre**, dati di tabelle ausiliari verranno sempre archiviati per un uso successivo.  
  
-   Se si seleziona **se il confronto tra le tabelle non è stato possibile salvare**, verranno archiviati i dati di tabelle ausiliari solo se si verifica un errore.  
  
-   Se si seleziona **Elimina sempre**, tabelle ausiliarie sempre eliminati dopo l'esecuzione dei test.  
  
-   Se si seleziona **utente chiedere se non è riuscita confronto tra le tabelle**, l'utente può selezionare le azioni necessarie se si verifica un errore.  
  
Fare clic sui **fine** consente di salvare il Test Case preparata in [repository Test utilizzando &#40;SybaseToSQL&#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Utilizzando Test repository &#40;SybaseToSQL&#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md)  
[Esecuzione di Test case &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Test di eseguire la migrazione di oggetti di Database &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
