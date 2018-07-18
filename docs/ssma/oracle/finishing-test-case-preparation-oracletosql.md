---
title: Completamento della preparazione del Test Case (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 32f38713-7ae4-48d3-980d-74cadc8545a0
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: cd91a80d322fb8048489ffead0bcbbeaf7e00c08
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984213"
---
# <a name="finishing-test-case-preparation-oracletosql"></a>Completamento della preparazione del Test Case (OracleToSQL)
Pagina finale della procedura guidata visualizza la descrizione del Test Case e le informazioni sugli oggetti coinvolti nel test. Inoltre, in questa pagina è possibile impostare il test di opzioni di esecuzione.  
  
Il **le informazioni di Test Case** sezione mostra il nome del Test Case e la descrizione.  
  
Il **gli oggetti selezionati per essere testati** sezione contiene l'elenco di oggetti testati raggruppati per tipo di oggetto denominato.  
  
Il **gli oggetti interessati dal Test che verranno analizzati** sezione consente di visualizzare l'elenco di oggetti quali modifiche di dati devono essere confrontati dopo l'esecuzione di oggetti testati denominato.  
  
## <a name="test-case-settings"></a>Impostazioni di test Case  
Nel **delle impostazioni di Test Case** sezione è possibile impostare le opzioni di test l'esecuzione della seguente:  
  
### <a name="stop-test-execution-after-first-failure"></a>Arrestare l'esecuzione di test dopo il primo errore  
Specifica per interrompere l'esecuzione del test se si verifica un errore durante l'esecuzione di test.  
  
-   Se si sceglie **Sì**, l'esecuzione di interrompe di test se si verifica un errore.  
  
-   Se si sceglie **No**, l'esecuzione di test continua dopo un errore.  
  
### <a name="perform-data-rollback"></a>Eseguire il rollback di dati  
Consente di eseguire il rollback automatico dei dati dopo l'esecuzione di test.  
  
-   Se si sceglie **Sì**, le modifiche ai dati andranno persi dopo l'esecuzione di test.  
  
-   Se si sceglie **No**, tutti i test verranno salvate le modifiche ai dati di esecuzione.  
  
### <a name="auxiliary-tables-saving-mode"></a>Tabelle ausiliarie modalità risparmio  
Definisce la modalità di salvataggio delle tabelle ausiliarie creato durante l'esecuzione di test. Vedere la descrizione delle tabelle ausiliarie nel [esecuzione di Test case &#40;OracleToSQL&#41; ](../../ssma/oracle/running-test-cases-oracletosql.md) argomento.  
  
-   Se si seleziona **salvare sempre**, verranno sempre archiviati dati di tabelle ausiliari per un uso successivo.  
  
-   Se si seleziona **se il confronto di tabella non è stato possibile salvare**, verranno archiviati i dati di tabelle ausiliari solo se si verifica un errore.  
  
-   Se si seleziona **sempre eliminare**, tabelle ausiliarie sempre eliminato dopo l'esecuzione di test.  
  
-   Se si seleziona **porre utente se non è stato possibile confronto tra le tabelle**, l'utente può selezionare le azioni necessarie se si verifica un errore.  
  
Fare clic sui **Finish** consente di salvare il Test Case preparata in [usando i repository Test (OracleToSQL)](http://msdn.microsoft.com/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4).  
  
## <a name="see-also"></a>Vedere anche  
[Uso di repository Test &#40;OracleToSQL&#41;](../../ssma/oracle/using-test-repositories-oracletosql.md)  
[Esecuzione di Test case &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test di oggetti di Database migrati &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
