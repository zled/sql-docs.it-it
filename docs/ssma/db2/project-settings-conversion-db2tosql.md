---
title: Impostazioni (conversione) (DB2ToSQL) del progetto | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 538c93cf-c5bb-43d5-b758-186d9fb00c19
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5ad3409125f4e6862304e02f05b03bcf821923ba
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="project-settings-conversion-db2tosql"></a>Impostazioni del progetto (conversione) (DB2ToSQL)
La pagina di conversione del **impostazioni progetto** la finestra di dialogo contiene le impostazioni che consentono di personalizzare come SSMA Converte la sintassi per DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi.  
  
Il riquadro di conversione è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo:  
  
-   Per specificare le impostazioni per tutti i progetti SSMA, il **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa, quindi fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **conversione**.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** dal menu **impostazioni progetto**, quindi fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **conversione**.  
  
## <a name="conversion-messages"></a>Messaggi di conversione  
  
### <a name="generate-messages-about-issues-applied"></a>Generazione di messaggi sui problemi applicati  
Specifica se SSMA genera messaggi informativi durante la conversione, vengono visualizzate nel riquadro di Output e li aggiunge al codice convertito.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**La modalità predefinita/ottimistico:** No  
  
**Modalità completa:** No  
  
## <a name="miscellaneous-options"></a>Opzioni varie  
  
### <a name="cast-rownum-expressions-as-integers"></a>Espressioni ROWNUM cast come numeri interi  
Quando SSMA converte le espressioni ROWNUM, l'espressione viene convertita in una clausola TOP, seguita dall'espressione. Nell'esempio seguente viene illustrato ROWNUM in un'istruzione DELETE DB2:  
  
`DELETE FROM Table1`  
  
`WHERE ROWNUM < expression and Field1 >= 2`  
  
L'esempio seguente mostra il valore risultante [!INCLUDE[tsql](../../includes/tsql_md.md)]:  
  
`DELETE TOP (expression-1)`  
  
`FROM Table1`  
  
`WHERE Field1>=2`  
  
Nella parte superiore, è necessario che l'espressione di clausole TOP restituisce un numero intero. Se il numero intero negativo, l'istruzione genererà un errore.  
  
-   Se si seleziona **Sì**, SSMA esegue il cast dell'espressione come un numero intero.  
  
-   Se si seleziona **n**, SSMA contrassegnerà tutte le espressioni non integer come un errore nel codice convertito.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Full:** No  
  
**La modalità ottimistico:** Sì  
  
### <a name="default-schema-mapping"></a>Mapping dello Schema predefinito  
Questa impostazione specifica la modalità di mapping degli schemi di DB2 agli schemi di SQL Server. Sono disponibili in questa impostazione di due opzioni:  
  
1.  **Schema per database:** In questa modalità DB2 lo schema 'sch1' verrà mappato per impostazione predefinita allo schema di SQL Server 'dbo' nel database di SQL Server 'sch1'.  
  
2.  **Schema allo schema:** In questa modalità DB2 lo schema 'sch1' verrà mappato per impostazione predefinita allo schema di SQL Server 'sch1' nel database di SQL Server predefinito fornito nella finestra di dialogo di connessione.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic/Full:** Schema al database  
  
### <a name="conversion-ways-of-merge-statement"></a>Modalità di conversione dell'istruzione MERGE  
  
-   Se si seleziona **utilizzo dell'istruzione INSERT, UPDATE, istruzione DELETE**SSMA Converte l'istruzione di unione in INSERT, UPDATE, DELETE istruzioni.  
  
-   Se si seleziona **istruzione utilizzando MERGE**, SSMA Converte l'istruzione di unione in istruzione MERGE in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
> [!WARNING]  
> Questa opzione di impostazione di progetto è disponibile solo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic/Full:** Using MERGE istruzione  
  
### <a name="convert-calls-to-subprograms-that-use-default-arguments"></a>Convertire le chiamate a sottoprogrammi che usano argomenti predefiniti  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] funzioni non supportano l'omissione dei parametri nella chiamata di funzione. Inoltre, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] procedure e funzioni non supportano espressioni come valori di parametro predefiniti.  
  
-   Se si seleziona **Sì** e una chiamata di funzione include parametri, inserirà la parola chiave SSMA **predefinito** in cui la funzione e una chiamata nella posizione corretta. Contrassegna quindi la chiamata con un messaggio di avviso.  
  
-   Se si seleziona **n**, SSMA verrà contrassegnate come le chiamate di funzione come errori.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Sì  
  
### <a name="convert-count-function-to-countbig"></a>Convertire funzione COUNT con COUNT_BIG  
Se le funzioni di conteggio sono probabile restituire i valori superiori a 2.147.483.647, ovvero 2<sup>31</sup>-1, è consigliabile convertire le funzioni in COUNT_BIG.  
  
-   Se si seleziona **Sì**, SSMA convertirà tutte le occorrenze del conteggio COUNT_BIG.  
  
-   Se si seleziona **n**, le funzioni rimarrà come conteggio. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] verrà restituito un errore se la funzione restituisce un valore più grande di 2<sup>31</sup>-1.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Full:** Sì  
  
**La modalità ottimistico:** No  
  
### <a name="convert-forall-statement-to-while-statement"></a>Convertire istruzione FORALL WHILE istruzione  
Definisce il modo SSMA tratterà FORALL cicli sugli elementi della raccolta di PL/SQL.  
  
-   Se si seleziona **Sì**, SSMA crea un ciclo WHILE in cui gli elementi della raccolta vengono recuperati uno alla volta.  
  
-   Se si seleziona **n**, SSMA genera un set di righe dalla raccolta utilizzando il metodo di () i nodi e viene utilizzato come una singola tabella. È più efficiente, ma rende meno leggibile il codice di output.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**La modalità predefinita/ottimistico:** No  
  
**Modalità completa:** Sì  
  
### <a name="convert-foreign-keys-with-set-null-referential-action-on-column-that-is-not-null"></a>Convertire le chiavi esterne con l'operazione referenziale SET NULL nella colonna non NULL.  
DB2 consente la creazione di vincoli di chiave esterna, in cui una SET NULL potrebbe eventualmente eseguire l'operazione perché non sono consentiti valori null nella colonna a cui fa riferimento. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non consente tale configurazione della chiave esterna.  
  
-   Se si seleziona **Sì**, SSMA genererà referenziali come DB2, ma sarà necessario apportare modifiche manuali prima di caricare il vincolo [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Ad esempio, è possibile scegliere NO ACTION anziché SET NULL.  
  
-   Se si seleziona **n**, il vincolo verrà contrassegnato come errore.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** No  
  
### <a name="convert-function-calls-to-procedure-calls"></a>Convertire le chiamate di funzione per le chiamate di procedura  
Alcune funzioni DB2 sono definiti come transazioni autonomi o contengono le istruzioni che non sono valide in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. In questi casi, SSMA crea una stored procedure e una funzione che è un wrapper per la procedura. La funzione convertita chiama la procedura di implementazione.  
  
SSMA è possibile convertire le chiamate alla funzione wrapper in chiamate di procedura. Questo consente di creare codice più leggibile e può migliorare le prestazioni. Tuttavia, il contesto non sempre consente. è ad esempio, non è possibile sostituire una chiamata di funzione nell'elenco di selezione con una chiamata di routine. SSMA presenta alcune opzioni per coprire i casi comuni:  
  
-   Se si seleziona **sempre**, SSMA tenta di convertire le chiamate di funzione wrapper in chiamate di procedura. Se il contesto corrente non consente la conversione, viene generato un messaggio di errore. In questo modo, nessuna chiamata di funzione viene lasciata nel codice generato.  
  
-   Se si seleziona **quando possibile**, SSMA esegue uno spostamento a chiamate di procedura solo se la funzione ha parametri di output. Quando lo spostamento non è possibile, viene rimosso l'attributo di output del parametro. In tutti gli altri casi SSMA lascia le chiamate di funzione.  
  
-   Se si seleziona **mai**, SSMA lascerà tutte le chiamate di funzione come chiamate di funzione. In alcuni casi questa scelta non sarebbe accettabile per motivi di prestazioni.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic/Full:** quando possibile  
  
### <a name="convert-lock-table-statements"></a>Convertire le istruzioni di blocco tabella  
SSMA è possibile convertire numerose istruzioni di blocco tabella in hint di tabella. SSMA non è possibile convertire le istruzioni di blocco tabella che contengono una partizione, parte, @dblinke le clausole NOWAIT e verranno contrassegnate come tali istruzioni con messaggi di errore di conversione.  
  
-   Se si seleziona **Sì**, SSMA convertirà supportate le istruzioni di blocco TABLE in hint di tabella.  
  
-   Se si seleziona **n**, SSMA contrassegnerà tutte le istruzioni di blocco tabella con i messaggi di errore di conversione.  
  
Nella tabella seguente viene illustrato come SSMA converte le modalità di blocco DB2:  
  
|||  
|-|-|  
|DB2 Modalità di blocco|Hint di tabella SQL Server|  
|CONDIVISIONE DI RIGA|ROWLOCK, HOLDLOCK|  
|RIGA ESCLUSIVO|HOLDLOCK ROWLOCK, XLOCK,|  
|AGGIORNAMENTO DI CONDIVISIONE = CONDIVISIONE DI RIGA|ROWLOCK, HOLDLOCK|  
|CONDIVIDI|TABLOCK, HOLDLOCK|  
|CONDIVISIONE DI RIGA ESCLUSIVO|HOLDLOCK TABLOCK, XLOCK,|  
|ESCLUSIVO|TABLOCKX, HOLDLOCK|  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Sì  
  
### <a name="convert-open-for-statements-for-ref-cursor-out-parameters"></a>Convertire aperta per le istruzioni per i parametri REF CURSOR OUT  
In DB2, è possibile utilizzare l'istruzione OPEN per restituire un set di risultati a un parametro di tipo REF CURSOR OUT del sottoprogramma. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], le stored procedure restituire direttamente i risultati delle istruzioni SELECT.  
  
SSMA è possibile convertire numerose istruzioni OPEN FOR in istruzioni SELECT.  
  
-   Se si seleziona **Sì**, SSMA Converte l'istruzione OPEN FOR in un'istruzione SELECT, che restituisce il set di risultati al client.  
  
-   Se si seleziona **n**, SSMA genererà un messaggio di errore nel codice convertito e nel riquadro di Output.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Sì  
  
### <a name="convert-record-as-a-list-of-separates-variables"></a>Convertire i record come un elenco di variabili separa  
SSMA possibile convertire i record di DB2 in variabili separa e nelle variabili XML con struttura specifica.  
  
-   Se si seleziona **Sì**, SSMA converte il record in un elenco di variabili separa quando possibile.  
  
-   Se si seleziona **n**, SSMA converte il record in variabili XML con struttura specifica.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Sì  
  
### <a name="convert-substr-function-calls-to-substring-function-calls"></a>Convertire le chiamate di funzione SUBSTR alle chiamate di funzione SUBSTRING  
SSMA può convertire le chiamate di funzione SUBSTR DB2 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **sottostringa** chiamate di funzioni, a seconda del numero di parametri. Se SSMA non è possibile convertire una chiamata di funzione SUBSTR o il numero di parametri non è supportato, SSMA convertirà la chiamata di funzione SUBSTR in una chiamata di funzione SSMA personalizzata.  
  
-   Se si seleziona **Sì**, SSMA convertirà chiamate di funzione SUBSTR utilizzano tre parametri in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **sottostringa**. Altre funzioni SUBSTR verranno convertite per chiamare la funzione SSMA personalizzata.  
  
-   Se si seleziona **n**, SSMA convertirà la chiamata di funzione SUBSTR in una chiamata di funzione SSMA personalizzata.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**La modalità predefinita/ottimistico:** Sì  
  
**Modalità completa:** No  
  
### <a name="convert-subtypes"></a>Convertire sottotipi  
SSMA è possibile convertire sottotipi PL/SQL in due modi:  
  
-   Se si seleziona **Sì**, creerà SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] definito dall'utente tipo da un sottotipo e utilizzarlo per ogni variabile del sottotipo.  
  
-   Se si seleziona **n**, SSMA verrà sostituire tutte le dichiarazioni di origine del sottotipo di con il tipo sottostante e convertire il risultato come di consueto. In questo caso, non i tipi aggiuntivi vengono creati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** No  
  
### <a name="convert-synonyms"></a>Converte i sinonimi  
Sinonimi per gli oggetti di DB2 seguenti possono essere migrati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:  
  
-   Le tabelle e oggetto  
  
-   Viste e le viste di oggetto  
  
-   Stored procedure e funzioni  
  
-   Viste materializzate  
  
Sinonimi per gli oggetti di DB2 seguenti possono essere sostituiti da riferimenti diretti agli oggetti:  
  
-   Sequenze  
  
-   Pacchetti  
  
-   Oggetti dello schema di classe Java  
  
-   Tipi di oggetto definito dall'utente  
  
Impossibile eseguire la migrazione di altri sinonimi. SSMA genererà messaggi di errore per il sinonimo e tutti i riferimenti che usano il sinonimo.  
  
-   Se si seleziona **Sì**, creerà SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sinonimi e riferimenti a oggetti direttamente in base agli elenchi precedenti.  
  
-   Se si seleziona **n**, SSMA creerà i riferimenti agli oggetti direct per tutti i sinonimi elencati di seguito.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Sì  
  
### <a name="convert-tochardate-format"></a>Convertire TO_CHAR (date, formato)  
SSMA è possibile convertire TO_CHAR(date, format) DB2 in procedure dal database sysdb.  
  
-   Se si seleziona **funzione TO_CHAR_DATE utilizzando**, SSMA converte TO_CHAR (date, formato) in TO_CHAR_DATE funzione tramite della lingua inglese per la conversione.  
  
-   Se si seleziona **funzione utilizzando TO_CHAR_DATE_LS (attenzione NLS)**, SSMA converte TO_CHAR (date, formato) in TO_CHAR_DATE_LS funzione tramite della lingua di sessione per la conversione  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** Using TO_CHAR_DATE (funzione)  
  
**Modalità completa:** Using TO_CHAR_DATE_LS (NLS care) (funzione)  
  
### <a name="convert-transaction-processing-statements"></a>Convertire le istruzioni di elaborazione delle transazioni  
SSMA è possibile convertire le istruzioni di elaborazione delle transazioni DB2:  
  
-   Se si seleziona **Sì**, SSMA converte le istruzioni di elaborazione delle transazioni DB2 per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istruzioni.  
  
-   Se si seleziona **n**, SSMA contrassegna la transazione di errori di conversione di istruzioni di elaborazione.  
  
> [!NOTE]  
> DB2 apre le transazioni in modo implicito. Per emulare questo comportamento nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è necessario aggiungere manualmente le istruzioni BEGIN TRANSACTION in cui si desidera avviare le transazioni. In alternativa, è possibile eseguire il comando SET IMPLICIT_TRANSACTIONS ON all'inizio della sessione. SSMA aggiunge automaticamente i SET IMPLICIT_TRANSACTIONS ON durante la conversione subroutine con transazioni autonome.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Sì  
  
### <a name="emulate-db2-null-behavior-in-order-by-clauses"></a>Emulare il comportamento di null DB2 nelle clausole ORDER BY  
I valori NULL vengono ordinati in modo diverso in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e DB2:  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], NULL i valori sono i valori più bassi in un elenco ordinato. In un elenco crescente, verranno visualizzati per primi i valori NULL.  
  
-   In DB2, i valori NULL sono i valori più elevati in un elenco ordinato. Per impostazione predefinita, i valori NULL visualizzato per ultimi in un elenco in ordine crescente.  
  
-   DB2 con le clausole di valori null e i valori null cognome, che consente di modificare la modalità DB2 Ordina i valori null.  
  
SSMA è possibile emulare DB2 ORDER BY comportamento tramite il controllo dei valori NULL. Quindi innanzitutto gli ordini da valori NULL nell'ordine specificato, quindi viene ordini da altri valori.  
  
-   Se si seleziona **Sì**, SSMA convertirà l'istruzione di DB2 in modo che emula il comportamento di DB2 ORDER BY.  
  
-   Se si seleziona **n**, SSMA ignorerà le regole di DB2 e generare un messaggio di errore quando rileva le clausole di valori null e i valori null cognome.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**La modalità predefinita/ottimistico:** No  
  
**Modalità completa:** Sì  
  
### <a name="emulate-row-count-exceptions-in-select"></a>Emulare le eccezioni di conteggio righe in SELECT  
Se un'istruzione SELECT con una clausola INTO non restituisce alcuna riga, DB2 genera un'eccezione NO_DATA_FOUND. Se l'istruzione restituisce due o più righe, viene generato l'eccezione TOO_MANY_ROWS. L'istruzione convertita in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non genera un'eccezione se il conteggio delle righe è diverso da uno.  
  
-   Se si seleziona **Sì**, SSMA aggiunge chiamata a sysdb procedure db_error_exact_one_row_check dopo ogni istruzione SELECT. Questa procedura emula la NO_DATA_FOUND e TOO_MANY_ROWS le eccezioni. Questa è l'impostazione predefinita e consente di riprodurre il comportamento di DB2 più vicino possibile. È necessario selezionare sempre **Sì** se il codice sorgente ha gestori delle eccezioni che elaborano questi errori. Si noti che se l'istruzione SELECT si verifica all'interno di una funzione definita dall'utente, questo modulo verrà convertito in una stored procedure, poiché l'esecuzione di stored procedure e la generazione di eccezioni non è compatibile con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] contesto di funzione.  
  
-   Se si seleziona **n**, verranno generata alcuna eccezione. Che può essere utile quando SSMA converte una funzione definita dall'utente e si desidera rimanga una funzione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Sì  
  
### <a name="generate-error-for-dbmssqlparse"></a>Genera l'errore per DBMS_SQL. ANALISI  
  
-   Se si seleziona **errore**, SSMA genera l'errore di conversione DBMS_SQL. ANALISI.  
  
-   Se si seleziona **avviso**, SSMA Genera avviso per la conversione DBMS_SQL. ANALISI.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** errore  
  
### <a name="generate-rowid-column"></a>Genera colonna ROWID  
Quando di crea tabelle SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile creare una colonna ROWID. Quando viene eseguita la migrazione di dati, ogni riga Ottiene un nuovo valore UNIQUEIDENTIFIER generato dalla funzione NEWID ().  
  
-   Se si seleziona **Sì**, la colonna ROWID viene creata in tutte le tabelle e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] genera i GUID quando si inseriscono i valori. Scegliere sempre **Sì** se si prevede di utilizzare il Tester di SSMA.  
  
-   Se si seleziona **n**, ROWID non vengono aggiunte alle tabelle.  
  
-   **Aggiungere la colonna ROWID per le tabelle con trigger** aggiungere ROWID per le tabelle contenenti i trigger.  
  
> [!WARNING]  
> Impostazione predefinita nel caso di SQL Server 2005, SQL Server 2008 e SQL Server 2012 e 2014 **colonna aggiungere ROWID per le tabelle con trigger**.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** Aggiungi colonna ROWID per le tabelle con trigger  
  
**Modalità completa:** Sì  
  
### <a name="generate-unique-index-on-rowid-column"></a>Generare un indice univoco sulla colonna ROWID  
Specifica se SSMA genera colonna indice univoco sulla colonna ROWID generato o non. Se l'opzione è impostata su "Sì", viene generato l'indice univoco e se è impostato su "NO", l'indice univoco non viene generato sulla colonna ROWID.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Sì  
  
### <a name="local-modules-conversion"></a>Conversione di moduli locali  
Definisce il tipo di conversione di DB2 annidati sottoprogramma (dichiarato in autonoma stored procedure o funzione).  
  
-   Se si seleziona **Inline**, le chiamate nidificate sottoprogramma verranno sostituite dal proprio corpo.  
  
-   Se si seleziona **Stored procedure**sottoprogramma nidificato verrà convertito in una stored procedure SQL Server e verranno sostituiti relative chiamate effettuate in questa chiamata di procedura.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Inline  
  
### <a name="use-isnull-in-string-concatenation"></a>Utilizzo di ISNULL nella concatenazione di stringhe  
DB2 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] restituire risultati diversi quando concatenazioni di stringa includono valori NULL. DB2 considera il valore NULL come un set di caratteri vuota. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Restituisce NULL.  
  
-   Se si seleziona **Sì**, SSMA sostituisce il carattere di concatenazione di DB2 (|) con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] carattere concatenazione (+). SSMA controlla inoltre le espressioni su entrambi i lati della concatenazione dei valori NULL.  
  
-   Se si seleziona **n**, SSMA sostituisce i caratteri di concatenazione, ma non verifica la presenza di valori NULL.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
### <a name="use-isnull-in-replace-function-calls"></a>Utilizzo di ISNULL in chiamate di funzione REPLACE  
Istruzione di ISNULL viene utilizzata in chiamate di funzione REPLACE per emulare il comportamento di DB2. Le opzioni seguenti sono presenti per questa impostazione:  
  
-   YES  
  
-   No  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**La modalità predefinita/ottimistico:** No  
  
**Modalità completa:** Sì  
  
### <a name="use-isnull-in-concat-function-calls"></a>Utilizzo di ISNULL in chiamate di funzione CONCAT  
Istruzione di ISNULL viene utilizzata in chiamate di funzione CONCAT per emulare il comportamento di DB2. Le opzioni seguenti sono presenti per questa impostazione:  
  
-   YES  
  
-   No  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**La modalità predefinita/ottimistico:** No  
  
**Modalità completa:** Sì  
  
### <a name="use-native-convert-function-when-possible"></a>Utilizzare la funzione di conversione nativa quando possibile  
  
-   Se si seleziona **Sì**, SSMA converte TO_CHAR (date, formato) in funzione di conversione nativa quando possibile.  
  
-   Se si seleziona **n**, SSMA converte TO_CHAR (date, formato) in TO_CHAR_DATE o TO_CHAR_DATE_LS (è definito dalle opzioni di "Convertire TO_CHAR(date, format)").  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**La modalità predefinita/ottimistico:** Sì  
  
**Modalità completa:** No  
  
### <a name="use-selectfor-xml-when-converting-selectinto-for-record-variable"></a>Usare SELECT... FOR XML durante la conversione Seleziona... INTO per una variabile di record  
Specifica se generare un risultato XML impostato quando si seleziona in una variabile del record.  
  
-   Se si seleziona **Sì**, l'istruzione SELECT restituisce XML.  
  
-   Se si seleziona **n**, l'istruzione SELECT restituisce un set di risultati.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** No  
  
## <a name="returning-clause-conversion"></a>RESTITUZIONE di conversione clausola  
  
### <a name="convert-returning-clause-in-delete-statement-to-output"></a>Convertire l'OUTPUT clausola RETURNING nell'istruzione DELETE  
DB2 fornisce una clausola RETURNING come un modo per ottenere immediatamente valori eliminati. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] fornisce la funzionalità con la clausola OUTPUT.  
  
-   Se si seleziona **Sì**, SSMA convertirà RETURNING clausole nelle istruzioni DELETE per le clausole OUTPUT. Poiché i trigger in una tabella è possono modificare i valori, il valore restituito potrebbe essere diverso in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] rispetto a quello in DB2.  
  
-   Se si seleziona **n**, SSMA genererà un'istruzione SELECT prima di istruzioni DELETE per recuperare i valori restituiti.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Sì  
  
### <a name="convert-returning-clause-in-insert-statement-to-output"></a>Convertire l'OUTPUT clausola RETURNING nell'istruzione INSERT  
DB2 fornisce una clausola RETURNING come un modo per ottenere immediatamente i valori inseriti. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] fornisce la funzionalità con la clausola OUTPUT.  
  
-   Se si seleziona **Sì**, SSMA convertirà una clausola RETURNING in un'istruzione INSERT per l'OUTPUT. Poiché i trigger in una tabella è possono modificare i valori, il valore restituito potrebbe essere diverso in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] rispetto a quello in DB2.  
  
-   Se si seleziona **n**, SSMA emula la funzionalità di DB2 mediante l'inserimento e quindi selezionando valori da una tabella di riferimento.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Sì  
  
### <a name="convert-returning-clause-in-update-statement-to-output"></a>Convertire l'OUTPUT clausola RETURNING nell'istruzione UPDATE  
DB2 fornisce una clausola RETURNING come un modo per ottenere immediatamente i valori aggiornati. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] fornisce la funzionalità con la clausola OUTPUT.  
  
-   Se si seleziona **Sì**, SSMA convertirà RETURNING clausole nelle istruzioni UPDATE per le clausole OUTPUT. Poiché i trigger in una tabella è possono modificare i valori, il valore restituito potrebbe essere diverso in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] rispetto a quello in DB2.  
  
-   Se si seleziona **n**, SSMA genera le istruzioni SELECT dopo le istruzioni UPDATE per recuperare i valori di restituzione.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** Sì  
  
## <a name="sequence-conversion"></a>Conversione di sequenza  
  
### <a name="convert-sequence-generator"></a>Convertire il generatore di sequenze  
In DB2, è possibile utilizzare una sequenza per generare identificatori univoci.  
  
SSMA è possibile convertire le sequenze per le operazioni seguenti.  
  
-   Utilizzando il generatore di sequenze di SQL Server (questa opzione è disponibile solo durante la conversione a SQL Server 2012 e SQL Server 2014).  
  
-   Utilizzando il generatore di sequenze SSMA.  
  
-   Utilizzando l'identità di colonna.  
  
L'opzione predefinita quando si converte in SQL Server 2012 o SQL Server 2014 consiste nell'utilizzare il generatore di sequenze di SQL Server. Tuttavia, SQL Server 2012 e SQL Server 2014 non supporta ottenere il valore di sequenza corrente (ad esempio quella del metodo currval della sequenza di DB2). Fare riferimento al sito di blog del team SSMA per indicazioni sulla migrazione metodo currval della sequenza di DB2.  
  
SSMA fornisce inoltre un'opzione per convertire una sequenza di DB2 emulatore sequenza SSMA. Questo è l'opzione predefinita quando si converte in SQL Server precedente alla 2012  
  
Infine, è anche possibile convertire sequenza assegnato a una colonna nella tabella di valori identity di SQL Server. È necessario specificare il mapping tra le sequenze a una colonna identity in DB2 **tabella** scheda  
  
### <a name="convert-currval-outside-triggers"></a>Convertire CURRVAL all'esterno di trigger  
Visibile solo quando il generatore di sequenza convertire è impostato su **utilizzando l'identità di colonna**. Poiché le sequenze di DB2 sono oggetti distinti dalle tabelle, usano le sequenze di molte tabelle di utilizzano un trigger per generare e inserire un nuovo valore di sequenza. SSMA queste istruzioni come commento o li contrassegna come errori quando il commento fuori genererebbero errori.  
  
-   Se si seleziona **Sì**, SSMA verrà contrassegnati tutti i riferimenti ai trigger convertito di fuori sequenza CURRVAL con un messaggio di avviso.  
  
-   Se si seleziona **n**, SSMA verrà contrassegnati tutti i riferimenti ai trigger convertito di fuori sequenza CURRVAL con un errore.  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'interfaccia utente &#40;DB2ToSQL&#41;](../../ssma/db2/user-interface-reference-db2tosql.md)  
  
