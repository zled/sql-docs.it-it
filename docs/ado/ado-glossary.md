---
title: Glossario di ADO | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, glossary
ms.assetid: b0478836-4123-4357-969a-c5784fc28be5
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c5a423a72b173020a4e711cd2f6d1d2a7ba62fc
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271600"
---
# <a name="ado-glossary-terms"></a>Termini del Glossario ADO
In questo argomento definisce termini rilevanti per ADO.

## <a name="a"></a>Un
 Un URL completo URL assoluto che specifica il percorso di una risorsa che si trova su Internet o intranet. Vedere anche *URL* e *URL relativo*.

 Registrazione automatica, in-process componente COM che spesso include un elemento visivo in fase di progettazione o di esecuzione del controllo ActiveX. Controlli ActiveX sono inoltre in grado di comunicare con un contenitore di documenti attivi, ad esempio Microsoft Internet Explorer.

 ADISAPI (Advanced dati Internet Server Application Programming Interface) una DLL ISAPI che fornisce l'analisi, controllo di automazione, effettuare il marshalling Recordset e creazione del pacchetto MIME. Il componente ADISAPI funziona tramite l'API fornita da Internet Information Services (IIS). Vedere anche *ISAPI*.

 funzione di aggregazione In una query, una funzione, ad esempio COUNT, AVG o STDEV che calcola un valore utilizzando tutte le righe in una colonna di una tabella. La scrittura di espressioni e nella programmazione, è possibile utilizzare le funzioni di aggregazione SQL (inclusi i tre elencati in precedenza) e funzioni di aggregazione sui domini per determinare varie statistiche.

 Alias nome alternativo è assegnato a una colonna o espressione in un'istruzione SQL SELECT, spesso più breve o più significativa. Ad esempio, BobSales è l'alias nell'istruzione SELECT seguente: "Select SCR Sales as BobSales from SalesDB". Per assegnare dinamicamente le colonne per l'oggetto DataControl associazioni del controllo, è possibile utilizzare un alias.

 threading apartment COM di un modello di threading in cui si verificano tutte le chiamate a un oggetto in un unico thread. Nel threading apartment COM Sincronizza ed effettua il marshalling di chiamate. Vedere anche *COMmddefcom*.

 operazione asincrona di un'operazione che restituisce il controllo al programma chiamante senza attendere il completamento dell'operazione. Prima che l'operazione è stata completata, continua l'esecuzione del codice. Vedere anche *operazione sincrona*.

## <a name="b"></a>B
 mapping di una voce di associazione tra un campo in una tabella e una variabile. Nelle estensioni di Visual C++ ADO, **Recordset** campi vengono mappati a variabili di C/C++.

 valore numerico di una maschera di bit deve essere un confronto di valori di bit per bit con altri valori numerici, in genere alle opzioni di flag di parametri o valori restituiti. In genere questo confronto viene eseguito con gli operatori logici OR bit per bit, ad esempio **e** e **o** in Visual Basic **&** e **&#124;** in C++.

 Ad esempio, ADO **FieldAttributeEnum** valori possono essere utilizzati come maschere di bit per determinare gli attributi di un campo. Si supponga di che voler determinare se un campo non è aggiornabile. È possibile effettuare questa verifica con l'espressione seguente in Visual Basic:`Field.Attributes AND adFldUpdatable`

 Se il risultato è TRUE, il campo è aggiornabile.

 segnalibro un indicatore che identifica in modo univoco una riga all'interno di un set di righe in modo che un utente può passare rapidamente a esso.

 oggetto business un oggetto che esegue un set definito di operazioni, ad esempio la convalida dei dati o logica della regola business. Gli oggetti business si trovano in genere nel livello intermedio.

 regola di business la combinazione di modifiche di convalida, verifiche di accesso, ricerche nel database, i criteri e trasformazioni algoritmiche che costituiscono un'azienda di attività di business. Noto anche come *logica di business*.

## <a name="c"></a>c
 calcolato espressione un'espressione non costante, ma il cui valore dipende da altri valori. Per poter essere valutata un'espressione calcolata è necessario ottenere e calcolare i valori da altre origini, in genere in altri campi o righe.

 riferimento A capitoli a un intervallo di righe da un'origine dati. In ADO un capitolo viene in genere un riferimento a un altro **Recordset**.

 Le colonne a capitoli consentono di definire un *padre-figlio* relazione in cui il *padre* è il **Recordset** contenente la colonna a capitoli e  *figlio* è il **Recordset** rappresentato dal capitolo.

 alias di capitolo alias che fa riferimento alla colonna aggiunta all'elemento padre.

 Un mapping di un set di caratteri di set di caratteri in base ai valori numerici. Ad esempio, Unicode è un carattere a 16 bit impostato in grado di codifica di tutti i caratteri noti e utilizzato come standard di codifica dei caratteri in tutto il mondo.

 elemento figlio lato dipendente in una relazione gerarchica. Un elemento figlio è un nodo in una struttura gerarchica con un altro nodo precedente (più vicino alla radice). Vedere anche *figlio alias*, *relazione padre-figlio*, *padre*.

 alias di figlio alias che fa riferimento all'elemento figlio. Vedere anche *alias*, *figlio*.

 CLSID (identificatore di classe) un identificatore univoco universale (UUID) che identifica un componente COM. Ogni componente COM ha un proprio CLSID del Registro di sistema in modo che può essere caricato da altre applicazioni. Vedere anche *ProgID*, *COM*.

 livello logico di client A livello di un sistema distribuito che in genere le presenta dati ed elabora l'input dell'utente, detta anche il *front-end*. In genere, il livello client richiede i dati da un server in base all'input e quindi formatta e visualizza il risultato. Vedere anche *livello intermedio*, *il livello di origine dati*, *dell'applicazione distribuita*.

 COM (Component Object Model) A binario standard che consente l'interoperabilità degli oggetti in un ambiente di rete indipendentemente dal linguaggio in cui sono stati sviluppati o in quale computer si trovano. Tecnologie COM includono controlli ActiveX, automazione e il collegamento e incorporamento (OLE). Consente a un oggetto per esporne la funzionalità per gli altri componenti e applicazioni host. Definisce come l'oggetto espone sia il funzionamento di questa esposizione tra processi e nelle reti. COM definisce anche il ciclo di vita dell'oggetto.

 File binari del componente COM, ad esempio con estensione dll e ocx alcuni file .exe, che supporta lo standard di COM per fornire gli oggetti. Tale file contiene codice per uno o più class factory, classi COM, voci del Registro di sistema, il codice di caricamento e così via.

 operatore di confronto, un operatore che confronta due espressioni e restituisce un valore booleano.

 Un parametro di criteri che può essere espressi come ">" (maggiore di), "\<" (minore di), "=" (uguale), "> =" (maggiore o uguale a), "< =" (minore o uguale a), "<>" (non uguale), o "like" (criteri di ricerca).

 componente di un oggetto che incapsula i dati e codice e fornisce un set specifico di servizi disponibili pubblicamente.

 file composto un'implementazione di COM strutturato di archiviazione per i file. Un file composto Archivia oggetti separati in un file singolo, strutturato costituito da due elementi principali: gli oggetti di archiviazione e gli oggetti flusso. Insieme, questi funzionano come un file system in un file.

 Numero di singoli file associati in un file fisico. Tutti i singoli file in un file composto sono accessibili come se fosse un unico file fisico.

 costante un valore numerico o stringa che non cambia. Enumerazioni ADO denominate (costanti enumerate) consente ad esempio, nel codice anziché i valori effettivi, **adUseClient** è una costante il cui valore è 3. (Anche enumerazione = 3). Vedere anche *enumerazione*.

 cursore di un elemento di database che controlla la visibilità delle modifiche apportate al database da altri utenti, navigazione tra i record e aggiornabilità dei dati.

## <a name="d"></a>D
 Il processo di associazione di oggetti o controlli di un'applicazione a un'origine dati di associazione di dati. Un controllo associato a un'origine dati viene definito un *controllo con associazione a dati*.

 Il contenuto di un controllo con associazione a dati è associato ai valori da un database. Ad esempio, un controllo griglia a cui è associato un **Recordset** oggetto può essere aggiornato quando le righe il **Recordset** vengono aggiornati. Quando vengono recuperati i nuovi valori per il **Recordset**, nuovi valori vengono visualizzati nella griglia.

 il provider di dati Software che espone i dati a un'applicazione ADO direttamente o tramite un provider di servizi. Vedere anche provider del servizio.

 data shaping tecnica che utilizza una sintassi formalizzato (chiamato **forma language**) per definire un tipo specializzato **Recordset** oggetto (chiamato un *a forma di Recordset*) che contiene dati non solo, ma anche riferimenti ad altri **Recordset** oggetti e/o i valori calcolati in base a quelle altri **Recordset** oggetti.

 livello di logica A livello di un sistema distribuito che rappresenta un computer che esegue un sistema DBMS, ad esempio un database di SQL Server dell'origine dati. Vedere anche *livello client*, *livello intermedio*, *dell'applicazione distribuita*.

 Protocollo di trasmissione A DCOM che consente ai componenti COM comunicare direttamente tra loro attraverso una rete. Vedere anche *COM*, *componente*.

 DDL (Data Definition Language) le istruzioni SQL che definiscono, in contrapposizione per manipolare dati. Lo schema di un database viene creato o modificato con DDL. Ad esempio, **CREATE TABLE**, **CREATE INDEX**, **GRANT**, e **revocare** sono istruzioni SQL DDL.

 Un flusso di testo o binario di flusso predefinito (rappresentato da un **flusso** oggetto) associato **Record** o **Recordset** oggetti quando si utilizza provider OLE DB specifici ad esempio il Provider Microsoft OLE DB per la pubblicazione su Internet. Il flusso predefinito include in genere il contenuto di un file, ad esempio il codice HTML per la radice di un sito Web.

 programma di applicazione distribuita A scritto in modo che l'elaborazione può essere suddiviso in più computer in rete. In genere, un'applicazione distribuita è suddivisa presentazione, logica di business e dati, livelli o *livelli*. Vedere anche il livello client, livello intermedio, il livello di origine dati.

 disconnesso A Recordset **Recordset** oggetto in una cache del client che non dispone più di una connessione in tempo reale al server. Se l'origine dei dati è necessario accedere nuovamente per qualche motivo, ad esempio l'aggiornamento dei dati, la connessione deve essere ristabilita. Tuttavia, le raccolte, proprietà e metodi di un disconnesso **Recordset** è ancora possibile accedervi.

 DML (Data Manipulation Language) le istruzioni SQL che modificano, anziché per definire, i dati. I valori in un database sono selezionati e modificati tramite DML. Ad esempio, **inserire**, **aggiornamento**, **eliminare**, e **selezionare** istruzioni DML SQL.

 provider dell'origine documento una classe speciale di provider di gestione di cartelle e documenti. Quando un documento è rappresentato da un **Record** oggetto o una cartella di documenti è rappresentato da un **Recordset** dell'oggetto, il provider di origine del documento consente di popolare gli oggetti con un set univoco di campi che Descrive le caratteristiche del documento, anziché il documento stesso. Vedere anche i record di risorse.

 DSN (nome dell'origine dati) la raccolta di informazioni utilizzata per connettere l'applicazione a un database ODBC specifico. Gestione Driver ODBC utilizza queste informazioni per creare una connessione al database. Un DSN può essere archiviato in un file (DSN) o del Registro di sistema (DSN computer).

 proprietà dinamiche A proprietà specifiche di un provider di dati o il servizio di cursore. Il **proprietà** collection di un oggetto viene popolato automaticamente con questi ("dinamico"). Un oggetto non dispone di alcuna proprietà dinamiche fino a quando non è connesso a un'origine dati tramite un provider di dati specifico. Vedere anche dati provider, cursore.

## <a name="e"></a>E
 Elenco di un'enumerazione di costanti denominate. Valori enumerati non devono essere univoci. Tuttavia il nome di ogni valore deve essere univoco all'interno dell'ambito in cui è definita l'enumerazione. In ADO, le enumerazioni vengono utilizzate per il parametro numerico e valori restituiscono, per aggiungere un significato codice ADO e proteggere allo sviluppatore di valori numerici (che possono cambiare a seconda della versione). Ad esempio, per aprire un valore statico **Recordset**, utilizzare il **adOpenStatic** valore enumerato: `Recordset.Open ,,adOpenStatic`

 Detta anche *costante enumerata*. Vedere anche *costante*.

 evento di un'azione riconosciuta da un oggetto, per cui è possibile scrivere codice per rispondere. Gli eventi possono essere generati dall'esecuzione del comando, completamento della transazione, navigazione del recordset e gli aggiornamenti dei dati, tra le altre azioni. Vedere anche *gestore dell'evento*.

 gestore eventi un gestore eventi è il codice che viene eseguito quando si verifica un evento. Vedere anche l'evento.

## <a name="h"></a>H
 routine di un gestore che gestisce una condizione relativamente semplice o un'operazione, ad esempio gestione degli errori di dati o di ripristino.

 A Recordset gerarchici **Recordset** che contiene l'altra **Recordset**. Vedere anche data shaping, capitolo.

 Per ulteriori informazioni, vedere [accesso alle righe in un Recordset gerarchico](../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).

 gerarchia In generale, una gerarchia è una struttura di pertinenza con un alto livello e i livelli subordinati. In ADO, gerarchica **recordset** vengono utilizzati per rappresentare la relazione padre-figlio tra un record e un capitolo. Anche in ADO, **Record** e **flusso** oggetti consente di accedere alle strutture ad albero gerarchica, ad esempio cartelle e documenti. ADO MD include inoltre **gerarchia** oggetti per rappresentare una relazione tra i livelli di una dimensione in un cubo OLAP. Vedere anche recordset gerarchico, relazione padre-figlio, capitolo, struttura ad albero.

## <a name="i-l"></a>I-L
 Set ISAPI (Internet Server Application Programming Interface) di funzioni per i server Internet, ad esempio Windows NT® Server o Windows 2000 Server che esegue Microsoft® Internet Information Services (IIS).

 Chiave di una o più colonne in una tabella che identificano in modo univoco una riga. spesso usati per indicizzare una tabella.

## <a name="m"></a>M
 Il processo di creazione pacchetto, di invio e disassemblaggio interfaccia dei parametri del metodo di marshalling attraverso i limiti di thread o processo.

 Il livello logico in un sistema distribuito tra un'interfaccia utente o client Web e il database di livello intermedio. Si tratta in genere in cui vengono create istanze di oggetti business. Il livello intermedio è una raccolta di regole business e le funzioni che generano e operano alla ricezione di informazioni. Eseguite tramite le regole di business, che possono cambiare di frequente e pertanto vengono incapsulate in componenti che sono separati fisicamente dalla logica dell'applicazione stessa. Noto anche come *livello del server applicazioni*. Vedere anche applicazione distribuita, livello client, il livello di origine dati.

 Un protocollo MIME (estensione di posta elettronica Internet multifunzionale) sviluppato per consentire lo scambio di messaggi di posta elettronica con contenuto complesso tra rete eterogenea, computer e gli ambienti di posta elettronica. In pratica, MIME ha inoltre stato adottato ed esteso da applicazioni non di posta elettronica.

 MIME è uno standard che consente di dati binari da pubblicare e leggere in Internet. L'intestazione di un file con dati binari contiene il tipo MIME dei dati. informa i programmi client (browser Web e pacchetti di posta elettronica, ad esempio) che sarà necessario gestire i dati in modo diverso rispetto al testo normale. Ad esempio, l'intestazione di un documento Web contenente un'immagine JPEG contiene il tipo MIME specifico per il formato file JPEG. In questo modo un browser per visualizzare il file con il relativo visualizzatore JPEG, se presente.

## <a name="n-o"></a>N-O
 nodo di un elemento in una struttura ad albero gerarchica. Un nodo può essere la radice o figlio di un altro nodo. Un nodo può essere anche l'elemento padre di più figli. Vedere anche gerarchia, struttura ad albero, radice, figlio, padre.

 variabile di una variabile oggetto che contiene un riferimento a un oggetto. Ad esempio, `objCustomObject` è una variabile che punta a un oggetto di tipo CustomObject:`Set objCustomObject = CreateObject(adodb.Recordset)`

 ODBC (Open Database Connectivity) di un'interfaccia di linguaggio di programmazione standard utilizzato per connettersi a un'ampia gamma di origini dati. Questo avviene in genere tramite il pannello di controllo, in cui i nomi di origine dati (DSN) possono essere assegnati a specifici driver ODBC di utilizzare.

 OLE DB A set di interfacce da esporre i dati da un'ampia gamma di origini tramite COM. Le interfacce OLE DB di forniscono applicazioni con un accesso uniforme ai dati archiviati in diverse origini dati. Queste interfacce supportano la quantità di funzionalità DBMS appropriata per l'origine dati, consentendo di condividere i propri dati. Vedere anche COM.

 ottimistica il blocco di un tipo di blocco in cui la pagina di dati contenente uno o più record, incluso il record viene modificato, è disponibile per altri utenti solo quando il record viene aggiornato mediante la **aggiornamento** (metodo), ma è disponibile prima e dopo la chiamata a **aggiornamento**.

 Blocco ottimistico viene utilizzato quando il **Recordset** oggetto viene aperto con il **LockType** parametro o proprietà è impostata su **adLockOptimistic** o  **adLockBatchOptimistic**. Vedere anche il blocco pessimistico.

 valore ordinale posizione numerica di un elemento all'interno di un ordine. In una raccolta di ADO, il valore ordinale del primo elemento è zero (0). L'elemento successivo è uno (1) e così via.

## <a name="p"></a>P
 query di un comando con parametri o un comando che consente di impostare i valori dei parametri prima dell'esecuzione del comando. Ad esempio, una stringa SQL può essere parametrizzata incorporando marcatori di parametro nella stringa SQL (definito dal '?' caratteri). Quindi, l'applicazione specifica valori per ogni parametro ed esegue il comando.

 elemento padre, il controllo lato di una relazione gerarchica. In una struttura gerarchica, un elemento padre dispone di uno o più nodi figlio direttamente di sotto della gerarchia. Vedere anche alias padre, figlio e relazione padre-figlio.

 alias padre un alias che fa riferimento all'elemento padre. Vedere anche alias, l'elemento padre.

 relazione di una relazione padre-figlio in una struttura gerarchica in cui l'elemento padre è un livello superiore e direttamente associato a uno o più figli. Un elemento figlio è più in basso e deve avere un unico elemento padre. Vedere anche l'elemento padre e figlio.

 pessimistica il blocco di un tipo di blocco in cui la pagina contenente uno o più record, incluso il record viene modificato, non è disponibile ad altri utenti per garantire che verrà eseguito un aggiornamento. Comportamento di blocco pessimistico è definito dal provider OLE DB. In genere, i record vengono bloccati durante la modifica e rimangono disponibili finché il **aggiornamento** completamento del metodo.

 Blocco pessimistico è abilitato quando il **Recordset** oggetto viene aperto con il **LockType** parametro o proprietà è impostata su **adLockPessimistic**. Vedere anche il blocco ottimistico.

 il pool di ottimizzazione delle prestazioni basato sull'utilizzo di raccolte di pre-allocare risorse, ad esempio gli oggetti o le connessioni al database. È più efficiente per disegnare una risorsa esistente dal pool rispetto alla creazione di una nuova risorsa.

 Identificatore programmatico (ProgID) un nome univoco mappato al Registro di sistema di Windows da un'applicazione COM. Il ProgID per una connessione ADO è "ADODB. Connessione". Vedere anche CLSID, COM.

 proxy di un oggetto specifico dell'interfaccia che fornisce il marshalling dei parametri e la comunicazione richiesti da un client chiamare un oggetto di applicazione che è in esecuzione in un ambiente di esecuzione diverso, ad esempio in un thread diverso o in un altro processo. Il proxy con il client si trova e comunica con uno stub corrispondente si trova all'oggetto applicazione che viene chiamato. Vedere anche stub.

## <a name="r"></a>R
 URL relativo A parzialmente qualificati URL che specifica una risorsa in Internet o intranet il cui percorso è relativo a un punto di partenza specificato da un URL assoluto o un oggetto ADO Connection equivalente. In effetti, la concatenazione assoluto e relativo URL rappresentare un URL completo. Vedere anche URL e l'URL assoluto.

 Un'origine dati esistente in un altro computer, piuttosto che nel sistema locale (in esecuzione l'applicazione client) dell'origine dati remoti.

 record di risorse a un record da un provider di origine di documento che contiene i campi per la definizione e la descrizione di un documento o cartella. Il documento stesso non è contenuto nel record di risorse, ma in genere, è possibile accedere tramite il flusso predefinito o un campo del record di risorse contenente un URL. Vedere anche provider di origine di documenti, flusso predefinito, URL.

 set di righe A set di righe da un'origine dati, tutti con lo stesso schema del campo. Un set di righe può rappresentare tutti o alcuni campi da una tabella. Un set di righe può anche rappresentare una tabella virtuale, creata da una query o di un join di due o più tabelle. In ADO, set di righe sono rappresentati da **Recordset** oggetti.

## <a name="s"></a>S
 Definire l'ambito dell'intervallo di riferimento per un oggetto o una variabile o un intervallo di record in una tabella o una vista. Le variabili locali, ad esempio, possono fare riferimento solo all'interno di routine in cui sono stati definiti. Le variabili pubbliche sono accessibili da qualsiasi punto dell'applicazione. Gli oggetti, ad esempio il database corrente, sono nell'ambito se nel percorso di ricerca definiti. Con una clausola di ambito in molti comandi, è possibile specificare gli intervalli dei record.

 provider di servizi Software che incapsula un servizio, creazione e utilizzo di dati, in modo da integrare le funzionalità delle applicazioni ADO. Si tratta di un provider che espone direttamente i dati, bensì fornisce un servizio, ad esempio l'elaborazione di query. Il provider del servizio può elaborare i dati forniti dal provider di dati. Vedere anche il provider di dati.

 la forma A Recordset **Recordset** le cui colonne sono state definite in modo specifico per contenere non solo dati, ma anche riferimenti, definiti capitoli, ad altre **Recordset** oggetti e/o i valori calcolati in base a altri **Recordset** oggetti.

 elemento di pari livello due o più nodi in una struttura gerarchica che sono allo stesso livello nella gerarchia. Il nodo radice in una gerarchia non ha elementi di pari livello.

 la stored procedura precompilato raccolta di codice, ad esempio istruzioni SQL e istruzioni di controllo di flusso facoltative archiviate con un nome ed elaborate come unità. Stored procedure vengono archiviate all'interno di un database. essi possono essere eseguite con un'unica chiamata da un'applicazione e consente le variabili dichiarate dall'utente, esecuzione condizionale e altre potenti funzionalità di programmazione.

 stub di un oggetto specifico dell'interfaccia che fornisce il marshalling dei parametri e la comunicazione necessarie per un oggetto di applicazione ricevere le chiamate da un client che è in esecuzione in un ambiente di esecuzione diverso, ad esempio in un thread diverso o in un altro processo. Lo stub con l'oggetto di applicazione si trova e comunica con un proxy corrispondente disponibile con il client che lo chiama. Vedere anche proxy.

 nodo secondario vedere figlio.

 inizio dell'operazione sincrona un'operazione avviata dal codice che viene completata prima dell'operazione successiva. Vedere anche l'operazione asincrona.

## <a name="t-z"></a>T-Z
 Struttura che rappresenta una relazione gerarchica tra gli elementi (nodi). È presente un nodo al livello superiore di una struttura ad albero (radice). Sotto la radice, possono essere presenti più figli. Ogni elemento figlio a sua volta potrebbe essere l'elemento padre di altri elementi figlio, pertanto la diramazione come una struttura ad albero. Una cartella contenente i documenti e altre cartelle è un esempio tipico di una struttura ad albero. Vedere anche gerarchia, nodo, radice, figlio, padre.

 Server Web un computer che fornisce i servizi Web e le pagine per utenti di Internet e intranet.
