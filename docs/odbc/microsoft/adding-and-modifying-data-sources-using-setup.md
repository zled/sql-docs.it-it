---
title: Aggiunta e modifica dati origini utilizzando il programma di installazione | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], adding
- editing data sources [ODBC], ODBC driver for Oracle
- adding data sources [ODBC], ODBC driver for Oracle
- data sources [ODBC], changing
- data sources [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], adding data sources
ms.assetid: 54b2d61d-6ce5-45af-a776-e03180470ecf
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d9533da991d1a50c9051b428490afacf2421efb0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="adding-and-modifying-data-sources-using-setup"></a>Aggiunta e modifica di origini dati utilizzando il programma di installazione
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Un'origine dati identifica un percorso ai dati che possono includere una libreria di rete, server, database e altri attributi, in questo caso, l'origine dati è il percorso a un database Oracle. Per connettersi a un'origine dati, gestione Driver controlla il Registro di sistema di Windows per informazioni di connessione specifiche.  
  
 La voce del Registro di sistema creata dall'amministratore origine dati ODBC viene usata per i driver ODBC e di gestione Driver ODBC. Questa voce contiene informazioni su ogni origine dati e il relativo driver. Prima di connettersi a un'origine dati, è necessario aggiungere le informazioni di connessione nel Registro di sistema.  
  
 Per aggiungere e configurare le origini dati, utilizzare il [Amministrazione origine dati ODBC](../../odbc/admin/odbc-data-source-administrator.md). L'amministratore ODBC Aggiorna le informazioni di connessione origine dati. Quando si aggiungono le origini dati, l'amministratore ODBC aggiornato le informazioni del Registro di sistema.  
  
### <a name="to-add-a-data-source-for-windows"></a>Per aggiungere un'origine dati per Windows  
  
1.  Aprire Amministrazione origine dati ODBC.  
  
2.  Nella finestra di dialogo Amministratore origine dati ODBC, fare clic su Aggiungi. Verrà visualizzata la finestra di dialogo Creazione nuova origine dati.  
  
3.  Selezionare Microsoft ODBC per Oracle e quindi fare clic su Fine. Verrà visualizzata la finestra di Microsoft ODBC per la finestra di dialogo programma di installazione di Oracle.  
  
4.  Nella casella Nome origine dati, digitare il nome dell'origine dati che si desidera accedere. Può essere qualsiasi nome desiderato.  
  
5.  Nella casella Descrizione, digitare la descrizione per il driver. Questo campo facoltativo descrive il driver di database che l'origine dati si connette a. Può essere qualsiasi nome desiderato.  
  
6.  Nella casella nome utente, digitare il nome utente del database (ID utente del database).  
  
7.  Nella finestra di Server, digitare l'Alias del Database o connettersi stringa per il motore di Oracle Server che si desidera accedere.  
  
8.  Fare clic su OK per aggiungere questa origine dati.  
  
> [!NOTE]  
>  Verrà visualizzata la finestra di dialogo di origini dati e l'amministratore ODBC Aggiorna le informazioni del Registro di sistema. L'utente un nome e la stringa digitata di connessione diventano i valori di connessione predefinito per questa origine dati quando ci si connette a esso.  
  
1.  Fare clic su Crea le opzioni più specifiche sul Driver ODBC per l'installazione di Oracle:  
  
    -   **Conversione** , fare clic su Seleziona per scegliere una funzione di conversione di dati caricati. Il valore predefinito è \<Nessun convertitore >.  
  
    -   **Prestazioni** , ovvero il osservazioni includere nella casella di controllo di funzioni di catalogo specifica se il driver restituisce colonne note per il [SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) set di risultati. Quando questo valore non è impostato, il Driver ODBC per Oracle fornisce un accesso più rapido.  
  
         I SINONIMI di includere nella casella di controllo delle colonne SQL specifica se il driver restituisce informazioni sulle colonne. **La dimensione del buffer** specifica la dimensione, in byte, allocata per i dati recuperati. Il driver ottimizza il recupero in modo che un recupero dal Server Oracle restituisca un numero di righe sufficiente per riempire un buffer della dimensione specificata. Valori più grandi tendono a migliorare le prestazioni durante il recupero di una grande quantità di dati.  
  
    -   **Personalizzazione** : l'applicazione ODBC DayOfWeek casella di controllo Standard consente di specificare se il set di risultati sarà conforme nel formato di giorno della settimana specificato ODBC (domenica = 1. Sabato = 7). Se questa casella di controllo è deselezionata, viene restituito il valore di Oracle specifiche delle impostazioni locali.  
  
         Il SQLDescribeCol **restituisce sempre un valore di precisione** casella di controllo specifica se il driver deve restituire un valore diverso da zero per il *cbColDef* argomento di **SQLDescribeCol**. Questo attributo di stringa di connessione si applica solo alle colonne in cui non sono presente alcuna scala definita Oracle, ad esempio calcolata numeriche colonne e le colonne definite come numero senza una precisione o scala. Oggetto **SQLDescribeCol** chiamata restituisce 130 per la precisione quando Oracle non vengono fornite le informazioni. Se questa casella di controllo è deselezionata, il driver restituirà 0 per questi tipi di colonne.  
  
2.  Fare clic su Aggiungi per aggiungere un'altra origine dati oppure fare clic su Chiudi per uscire dall'installazione.  
  
### <a name="to-modify-a-data-source-for-windows"></a>Per modificare un'origine dati per Windows  
  
1.  Aprire Amministrazione origine dati ODBC. Fare clic sulla scheda DSN appropriata.  
  
2.  Selezionare l'origine dati Oracle che si desidera modificare e quindi fare clic su Configura. Verrà visualizzata la finestra di Microsoft ODBC per la finestra di dialogo programma di installazione di Oracle.  
  
3.  Modificare i campi dell'origine dati applicabile e quindi fare clic su OK.  
  
 Dopo avere completato la modifica le informazioni contenute in questa finestra di dialogo, l'amministratore ODBC Aggiorna le informazioni del Registro di sistema.
