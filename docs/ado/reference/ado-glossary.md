---
title: Glossario di ADO | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ADO, glossary
ms.assetid: b0478836-4123-4357-969a-c5784fc28be5
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d38ec14d124bcf45c4eb22188f86849d95f0275
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283410"
---
# <a name="ado-glossary"></a>Glossario di ADO
In questo argomento definisce termini rilevanti per ADO.  
  
## <a name="a"></a>Un  
 URL assoluto  
 Un URL completo che specifica il percorso di una risorsa che si trova su Internet o intranet. Vedere anche *URL* e *URL relativo*.  
  
 Controllo ActiveX  
 Registrazione automatica, in-process componente COM che spesso include un elemento visivo in fase di progettazione o di esecuzione. Controlli ActiveX sono inoltre in grado di comunicare con un contenitore di documenti attivi, ad esempio Microsoft Internet Explorer.  
  
 ADISAPI (avanzate dati Internet Server Application Programming Interface)  
 Una DLL ISAPI che fornisce l'analisi, controllo di automazione, marshalling Recordset e creazione del pacchetto MIME. Il componente ADISAPI funziona tramite l'API fornita da Internet Information Services (IIS). Vedere anche *ISAPI*.  
  
 funzione di aggregazione  
 In una query, una funzione, ad esempio COUNT, AVG o STDEV che calcola un valore utilizzando tutte le righe in una colonna di una tabella. La scrittura di espressioni e nella programmazione, è possibile utilizzare le funzioni di aggregazione SQL (inclusi i tre elencati in precedenza) e funzioni di aggregazione sui domini per determinare varie statistiche.  
  
 alias  
 Nome alternativo assegnato a una colonna o espressione in un'istruzione SQL SELECT, spesso più breve o più significativa. Ad esempio, BobSales è l'alias nell'istruzione SELECT seguente: "Select SCR Sales as BobSales from SalesDB". Per assegnare dinamicamente le colonne per l'oggetto DataControl associazioni del controllo, è possibile utilizzare un alias.  
  
 threading apartment  
 Un modello di threading COM in cui si verificano tutte le chiamate a un oggetto in un unico thread. Nel threading apartment COM Sincronizza ed effettua il marshalling di chiamate. Vedere anche *COMmddefcom*.  
  
 operazione asincrona  
 Un'operazione che restituisce il controllo al programma chiamante senza attendere il completamento dell'operazione. Prima che l'operazione è stata completata, continua l'esecuzione del codice. Vedere anche *operazione sincrona*.  
  
## <a name="b"></a>B  
 voce di binding  
 Un mapping tra un campo in una tabella e una variabile. Nelle estensioni di Visual C++ ADO, **Recordset** campi vengono mappati a variabili di C/C++.  
  
 maschera di bit  
 Un valore numerico è progettato per un confronto bit per bit con gli altri valori numerici, in genere per contrassegnare le opzioni di parametro o valori restituiti. In genere questo confronto viene eseguito con gli operatori logici OR bit per bit, ad esempio **e** e **o** in Visual Basic **&** e **&#124;** in C++.  
  
 Ad esempio, ADO **FieldAttributeEnum** valori possono essere utilizzati come maschere di bit per determinare gli attributi di un campo. Si supponga di che voler determinare se un campo non è aggiornabile. È possibile effettuare questa verifica con l'espressione seguente in Visual Basic:`Field.Attributes AND adFldUpdatable`  
  
 Se il risultato è TRUE, il campo è aggiornabile.  
  
 segnalibro  
 Un indicatore che identifica in modo univoco una riga all'interno di un set di righe in modo che un utente può passare rapidamente a esso.  
  
 oggetto business  
 Oggetto che esegue un set definito di operazioni, ad esempio logica della regola business di convalida o di dati. Gli oggetti business si trovano in genere nel livello intermedio.  
  
 regola di Business  
 La combinazione di modifiche di convalida, verifiche di accesso, ricerche nel database, i criteri e trasformazioni algoritmiche che costituiscono un'azienda di attività di business. Noto anche come *logica di business*.  
  
## <a name="c"></a>c  
 Espressione calcolata  
 Un'espressione non costante, ma il cui valore dipende da altri valori. Per poter essere valutata un'espressione calcolata è necessario ottenere e calcolare i valori da altre origini, in genere in altri campi o righe.  
  
 capitolo  
 Un riferimento a un intervallo di righe da un'origine dati. In ADO un capitolo viene in genere un riferimento a un altro **Recordset**.  
  
 Le colonne a capitoli consentono di definire un *padre-figlio* relazione in cui il *padre* è il **Recordset** contenente la colonna a capitoli e  *figlio* è il **Recordset** rappresentato dal capitolo.  
  
 alias di capitolo  
 Un alias che fa riferimento alla colonna aggiunta all'elemento padre.  
  
 set di caratteri  
 Un mapping di un set di caratteri in base ai valori numerici. Ad esempio, Unicode è un carattere a 16 bit impostato in grado di codifica di tutti i caratteri noti e utilizzato come standard di codifica dei caratteri in tutto il mondo.  
  
 child  
 Il lato dipendente di una relazione gerarchica. Un elemento figlio è un nodo in una struttura gerarchica con un altro nodo precedente (più vicino alla radice). Vedere anche *figlio alias*, *relazione padre-figlio*, *padre*.  
  
 alias di figlio  
 Un alias che fa riferimento all'elemento figlio. Vedere anche *alias*, *figlio*.  
  
 CLSID (identificatore di classe)  
 Identificatore univoco universale (UUID) che identifica un componente COM. Ogni componente COM ha un proprio CLSID del Registro di sistema in modo che può essere caricato da altre applicazioni. Vedere anche *ProgID*, *COM*.  
  
 livello client  
 Livello logico di un sistema distribuito che in genere le presenta dati ed elabora l'input dell'utente, detta anche il *front-end*. In genere, il livello client richiede i dati da un server in base all'input e quindi formatta e visualizza il risultato. Vedere anche *livello intermedio*, *il livello di origine dati*, *dell'applicazione distribuita*.  
  
 COM (Component Object Model)  
 Standard binario che consente l'interoperabilità degli oggetti in un ambiente di rete indipendentemente dal linguaggio in cui sono stati sviluppati o in quale computer si trovano. Tecnologie COM includono controlli ActiveX, automazione e il collegamento e incorporamento (OLE). Consente a un oggetto per esporne la funzionalità per gli altri componenti e applicazioni host. Definisce come l'oggetto espone sia il funzionamento di questa esposizione tra processi e nelle reti. COM definisce anche il ciclo di vita dell'oggetto.  
  
 Componente COM  
 File binario, ad esempio con estensione dll e ocx alcuni file .exe, che supporta lo standard di COM per fornire gli oggetti. Tale file contiene codice per uno o più class factory, classi COM, voci del Registro di sistema, il codice di caricamento e così via.  
  
 operatore di confronto  
 Un operatore che confronta due espressioni e restituisce un valore booleano.  
  
 Un parametro di criteri che può essere espressi come ">" (maggiore di), "\<" (minore di), "=" (uguale), "> =" (maggiore o uguale a), "< =" (minore o uguale a), "<>" (non uguale), o "like" (criteri di ricerca).  
  
 componente  
 Oggetto che incapsula i dati e codice e fornisce un set specifico di servizi disponibili pubblicamente.  
  
 file compositi  
 Un'implementazione di COM strutturato di archiviazione per i file. Un file composto Archivia oggetti separati in un file singolo, strutturato costituito da due elementi principali: gli oggetti di archiviazione e gli oggetti flusso. Insieme, questi funzionano come un file system in un file.  
  
 Numero di singoli file associati in un file fisico. Tutti i singoli file in un file composto sono accessibili come se fosse un unico file fisico.  
  
 constant  
 Un valore numerico o stringa che non cambia. Enumerazioni ADO denominate (costanti enumerate) consente ad esempio, nel codice anziché i valori effettivi, **adUseClient** è una costante il cui valore è 3. (Anche enumerazione = 3). Vedere anche *enumerazione*.  
  
 cursor  
 Un elemento di database che controlla la visibilità delle modifiche apportate al database da altri utenti, navigazione tra i record e aggiornabilità dei dati.  
  
## <a name="d"></a>D  
 associazione dati  
 Il processo di associazione di oggetti o controlli di un'applicazione a un'origine dati. Un controllo associato a un'origine dati viene definito un *controllo con associazione a dati*.  
  
 Il contenuto di un controllo con associazione a dati è associato ai valori da un database. Ad esempio, un controllo griglia a cui è associato un **Recordset** oggetto può essere aggiornato quando le righe il **Recordset** vengono aggiornati. Quando vengono recuperati i nuovi valori per il **Recordset**, nuovi valori vengono visualizzati nella griglia.  
  
 provider di dati  
 Software che espone i dati a un'applicazione ADO direttamente o tramite un provider di servizi. Vedere anche provider del servizio.  
  
 data shaping  
 Una tecnica che usano una sintassi formalizzata (chiamato **forma language**) per definire un tipo specializzato **Recordset** oggetto (chiamato un *a forma di Recordset*) che non contiene solo dati, ma anche riferimenti ad altre **Recordset** oggetti e/o i valori calcolati in base a quelle altri **Recordset** oggetti.  
  
 livello di origine dati  
 Livello logico di un sistema distribuito che rappresenta un computer che esegue un sistema DBMS, ad esempio un database di SQL Server. Vedere anche *livello client*, *livello intermedio*, *dell'applicazione distribuita*.  
  
 DCOM  
 Un protocollo di rete che consente ai componenti COM comunicare direttamente tra loro attraverso una rete. Vedere anche *COM*, *componente*.  
  
 DDL (Data Definition Language)  
 Istruzioni SQL che definiscono, anziché per modificare, i dati. Lo schema di un database viene creato o modificato con DDL. Ad esempio, **CREATE TABLE**, **CREATE INDEX**, **GRANT**, e **revocare** sono istruzioni SQL DDL.  
  
 flusso predefinito  
 Un flusso di testo o binario (rappresentato da un **flusso** oggetto) che è associata a **Record** o **Recordset** oggetti quando si utilizza provider OLE DB specifici, ad esempio il Provider Microsoft OLE DB per la pubblicazione su Internet. Il flusso predefinito include in genere il contenuto di un file, ad esempio il codice HTML per la radice di un sito Web.  
  
 applicazione distribuita  
 Un programma scritto in modo che l'elaborazione può essere suddiviso in più computer in rete. In genere, un'applicazione distribuita è suddivisa presentazione, logica di business e dati, livelli o *livelli*. Vedere anche il livello client, livello intermedio, il livello di origine dati.  
  
 Disconnesso  
 Oggetto **Recordset** oggetto in una cache del client che non dispone più di una connessione in tempo reale al server. Se l'origine dei dati è necessario accedere nuovamente per qualche motivo, ad esempio l'aggiornamento dei dati, la connessione deve essere ristabilita. Tuttavia, le raccolte, proprietà e metodi di un disconnesso **Recordset** è ancora possibile accedervi.  
  
 DML (Data Manipulation Language)  
 Istruzioni SQL che modificano, anziché per definire, i dati. I valori in un database sono selezionati e modificati tramite DML. Ad esempio, **inserire**, **aggiornamento**, **eliminare**, e **selezionare** istruzioni DML SQL.  
  
 provider di origine di documenti  
 Una classe speciale di provider di gestione di cartelle e documenti. Quando un documento è rappresentato da un **Record** oggetto o una cartella di documenti è rappresentato da un **Recordset** dell'oggetto, il provider di origine del documento consente di popolare gli oggetti con un set univoco di campi che Descrive le caratteristiche del documento, anziché il documento stesso. Vedere anche i record di risorse.  
  
 DSN (nome dell'origine dati)  
 Raccolta di informazioni utilizzate per connettersi all'applicazione di un database ODBC specifico. Gestione Driver ODBC utilizza queste informazioni per creare una connessione al database. Un DSN può essere archiviato in un file (DSN) o del Registro di sistema (DSN computer).  
  
 proprietà dinamiche  
 Una proprietà specifica di un provider di dati o il servizio di cursore. Il **proprietà** collection di un oggetto viene popolato automaticamente con questi ("dinamico"). Un oggetto non dispone di alcuna proprietà dinamiche fino a quando non è connesso a un'origine dati tramite un provider di dati specifico. Vedere anche dati provider, cursore.  
  
## <a name="e"></a>E  
 Enumerazione  
 Un elenco di costanti denominate. Valori enumerati non devono essere univoci. Tuttavia il nome di ogni valore deve essere univoco all'interno dell'ambito in cui è definita l'enumerazione. In ADO, le enumerazioni vengono utilizzate per il parametro numerico e valori restituiscono, per aggiungere un significato codice ADO e proteggere allo sviluppatore di valori numerici (che possono cambiare a seconda della versione). Ad esempio, per aprire un valore statico **Recordset**, utilizzare il **adOpenStatic** valore enumerato: `Recordset.Open ,,adOpenStatic`  
  
 Detta anche *costante enumerata*. Vedere anche *costante*.  
  
 evento  
 Un'azione riconosciuta da un oggetto, per cui è possibile scrivere codice per rispondere. Gli eventi possono essere generati dall'esecuzione del comando, completamento della transazione, navigazione del recordset e gli aggiornamenti dei dati, tra le altre azioni. Vedere anche *gestore dell'evento*.  
  
 gestore dell'evento  
 Un gestore eventi è il codice che viene eseguito quando si verifica un evento. Vedere anche l'evento.  
  
## <a name="h"></a>H  
 gestore  
 Una routine che gestisce una condizione relativamente semplice o un'operazione, ad esempio gestione degli errori di dati o di ripristino.  
  
 Recordset gerarchico  
 Oggetto **Recordset** che contiene l'altra **Recordset**. Vedere anche data shaping, capitolo.  
  
 Per ulteriori informazioni, vedere [accesso alle righe in un Recordset gerarchico](../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
 gerarchia  
 In generale, una gerarchia è una struttura di pertinenza con un alto livello e i livelli subordinati. In ADO, gerarchica **recordset** vengono utilizzati per rappresentare la relazione padre-figlio tra un record e un capitolo. Anche in ADO, **Record** e **flusso** oggetti consente di accedere alle strutture ad albero gerarchica, ad esempio cartelle e documenti. ADO MD include inoltre **gerarchia** oggetti per rappresentare una relazione tra i livelli di una dimensione in un cubo OLAP. Vedere anche recordset gerarchico, relazione padre-figlio, capitolo, struttura ad albero.  
  
## <a name="i-l"></a>I-L  
 ISAPI (Internet Server Application Programming Interface)  
 Un set di funzioni per i server Internet, ad esempio Windows NT® Server o Windows 2000 Server che esegue Microsoft® Internet Information Services (IIS).  
  
 Key  
 Una o più colonne in una tabella che identificano in modo univoco una riga. spesso usati per indicizzare una tabella.  
  
## <a name="m"></a>M  
 marshalling  
 Il processo di creazione pacchetto, di invio e disassemblaggio parametri di metodo di interfaccia attraverso i limiti di thread o processo.  
  
 livello intermedio  
 Livello logico in un sistema distribuito tra un'interfaccia utente o client Web e il database. Si tratta in genere in cui vengono create istanze di oggetti business. Il livello intermedio è una raccolta di regole business e le funzioni che generano e operano alla ricezione di informazioni. Eseguite tramite le regole di business, che possono cambiare di frequente e pertanto vengono incapsulate in componenti che sono separati fisicamente dalla logica dell'applicazione stessa. Noto anche come *livello del server applicazioni*. Vedere anche applicazione distribuita, livello client, il livello di origine dati.  
  
 MIME (estensione di posta elettronica Internet multifunzione)  
 Protocollo Internet originariamente sviluppato per consentire lo scambio di messaggi di posta elettronica con contenuto complesso tra rete eterogenea, computer e gli ambienti di posta elettronica. In pratica, MIME ha inoltre stato adottato ed esteso da applicazioni non di posta elettronica.  
  
 MIME è uno standard che consente di dati binari da pubblicare e leggere in Internet. L'intestazione di un file con dati binari contiene il tipo MIME dei dati. informa i programmi client (browser Web e pacchetti di posta elettronica, ad esempio) che sarà necessario gestire i dati in modo diverso rispetto al testo normale. Ad esempio, l'intestazione di un documento Web contenente un'immagine JPEG contiene il tipo MIME specifico per il formato file JPEG. In questo modo un browser per visualizzare il file con il relativo visualizzatore JPEG, se presente.  
  
## <a name="n-o"></a>N-O  
 node  
 Un elemento in una struttura ad albero gerarchica. Un nodo può essere la radice o figlio di un altro nodo. Un nodo può essere anche l'elemento padre di più figli. Vedere anche gerarchia, struttura ad albero, radice, figlio, padre.  
  
 variabile oggetto  
 Variabile che contiene un riferimento a un oggetto. Ad esempio, `objCustomObject` è una variabile che punta a un oggetto di tipo CustomObject:`Set objCustomObject = CreateObject(adodb.Recordset)`  
  
 ODBC (Open Database Connectivity)  
 Standard lingua interfaccia di programmazione utilizzata per connettersi a un'ampia gamma di origini dati. Questo avviene in genere tramite il pannello di controllo, in cui i nomi di origine dati (DSN) possono essere assegnati a specifici driver ODBC di utilizzare.  
  
 OLE DB  
 Un set di interfacce da esporre i dati da un'ampia gamma di origini tramite COM. Le interfacce OLE DB di forniscono applicazioni con un accesso uniforme ai dati archiviati in diverse origini dati. Queste interfacce supportano la quantità di funzionalità DBMS appropriata per l'origine dati, consentendo di condividere i propri dati. Vedere anche COM.  
  
 blocco ottimistico  
 Tipo di blocco in cui la pagina di dati contenente uno o più record, incluso il record viene modificato, non è disponibile ad altri utenti solo mentre il record viene aggiornato dal **aggiornamento** (metodo), ma è disponibile prima e dopo il chiamata a **aggiornamento**.  
  
 Blocco ottimistico viene utilizzato quando il **Recordset** oggetto viene aperto con il **LockType** parametro o proprietà è impostata su **adLockOptimistic** o  **adLockBatchOptimistic**. Vedere anche il blocco pessimistico.  
  
 valore ordinale  
 Posizione numerica di un elemento all'interno di un ordine. In una raccolta di ADO, il valore ordinale del primo elemento è zero (0). L'elemento successivo è uno (1) e così via.  
  
## <a name="p"></a>P  
 comando con parametri  
 Una query o un comando che consente di impostare i valori dei parametri prima dell'esecuzione del comando. Ad esempio, una stringa SQL può essere parametrizzata incorporando marcatori di parametro nella stringa SQL (definito dal '?' caratteri). Quindi, l'applicazione specifica valori per ogni parametro ed esegue il comando.  
  
 padre  
 Il controllo lato di una relazione gerarchica. In una struttura gerarchica, un elemento padre dispone di uno o più nodi figlio direttamente di sotto della gerarchia. Vedere anche alias padre, figlio e relazione padre-figlio.  
  
 parent-alias  
 Un alias che fa riferimento all'elemento padre. Vedere anche alias, l'elemento padre.  
  
 relazione padre-figlio  
 Una relazione in una struttura gerarchica in cui l'elemento padre è un livello superiore e direttamente associato a uno o più figli. Un elemento figlio è più in basso e deve avere un unico elemento padre. Vedere anche l'elemento padre e figlio.  
  
 blocco pessimistico  
 Tipo di blocco in cui la pagina contenente uno o più record, incluso il record viene modificato, è disponibile ad altri utenti per garantire che verrà eseguito un aggiornamento. Comportamento di blocco pessimistico è definito dal provider OLE DB. In genere, i record vengono bloccati durante la modifica e rimangono disponibili finché il **aggiornamento** completamento del metodo.  
  
 Blocco pessimistico è abilitato quando il **Recordset** oggetto viene aperto con il **LockType** parametro o proprietà è impostata su **adLockPessimistic**. Vedere anche il blocco ottimistico.  
  
 il pool  
 Ottimizzazione delle prestazioni basata sull'utilizzo di raccolte di pre-allocare risorse, ad esempio gli oggetti o le connessioni al database. È più efficiente per disegnare una risorsa esistente dal pool rispetto alla creazione di una nuova risorsa.  
  
 Identificatore programmatico (ProgID)  
 Nome univoco mappato al Registro di sistema di Windows da un'applicazione COM. Il ProgID per una connessione ADO è "ADODB. Connessione". Vedere anche CLSID, COM.  
  
 Proxy  
 Un oggetto specifico dell'interfaccia che fornisce il marshalling dei parametri e la comunicazione richiesti da un client chiamare un oggetto di applicazione che è in esecuzione in un ambiente di esecuzione diverso, ad esempio in un thread diverso o in un altro processo. Il proxy con il client si trova e comunica con uno stub corrispondente si trova all'oggetto applicazione che viene chiamato. Vedere anche stub.  
  
## <a name="r"></a>R  
 URL relativo  
 URL parziale che specifica una risorsa in Internet o intranet il cui percorso è relativo a un punto di partenza specificato da un URL assoluto o un oggetto ADO Connection equivalente. In effetti, la concatenazione assoluto e relativo URL rappresentare un URL completo. Vedere anche URL e l'URL assoluto.  
  
 origine dati remota  
 Un'origine dati esistente in un altro computer, piuttosto che nel sistema locale (in esecuzione l'applicazione client).  
  
 record di risorse  
 Un record da un provider di origine di documento che contiene i campi per la definizione e la descrizione di un documento o cartella. Il documento stesso non è contenuto nel record di risorse, ma in genere, è possibile accedere tramite il flusso predefinito o un campo del record di risorse contenente un URL. Vedere anche provider di origine di documenti, flusso predefinito, URL.  
  
 set di righe  
 Un set di righe da un'origine dati, tutti con lo stesso schema del campo. Un set di righe può rappresentare tutti o alcuni campi da una tabella. Un set di righe può anche rappresentare una tabella virtuale, creata da una query o di un join di due o più tabelle. In ADO, set di righe sono rappresentati da **Recordset** oggetti.  
  
## <a name="s"></a>S  
 Ambito  
 L'intervallo di riferimento per un oggetto o variabile o un intervallo di record in una tabella o vista. Le variabili locali, ad esempio, possono fare riferimento solo all'interno di routine in cui sono stati definiti. Le variabili pubbliche sono accessibili da qualsiasi punto dell'applicazione. Gli oggetti, ad esempio il database corrente, sono nell'ambito se nel percorso di ricerca definiti. Con una clausola di ambito in molti comandi, è possibile specificare gli intervalli dei record.  
  
 provider di servizi  
 Software che incapsula un servizio, creazione e utilizzo di dati, in modo da integrare le funzionalità delle applicazioni ADO. Si tratta di un provider che espone direttamente i dati, bensì fornisce un servizio, ad esempio l'elaborazione di query. Il provider del servizio può elaborare i dati forniti dal provider di dati. Vedere anche il provider di dati.  
  
 Recordset con data shaping  
 Oggetto **Recordset** le cui colonne sono state definite in modo specifico per contenere non solo dati, ma anche riferimenti, definiti capitoli, ad altre **Recordset** oggetti e/o i valori calcolati in base alle altre **Recordset** oggetti.  
  
 pari livello  
 Due o più nodi in una struttura gerarchica che sono allo stesso livello nella gerarchia. Il nodo radice in una gerarchia non ha elementi di pari livello.  
  
 stored procedure  
 Raccolta precompilata di codice, ad esempio istruzioni SQL e istruzioni di controllo di flusso facoltative archiviate con un nome ed elaborate come unità. Stored procedure vengono archiviate all'interno di un database. essi possono essere eseguite con un'unica chiamata da un'applicazione e consente le variabili dichiarate dall'utente, esecuzione condizionale e altre potenti funzionalità di programmazione.  
  
 stub  
 Un oggetto specifico dell'interfaccia che fornisce il marshalling dei parametri e la comunicazione necessarie per un oggetto di applicazione ricevere le chiamate da un client che è in esecuzione in un ambiente di esecuzione diverso, ad esempio in un thread diverso o in un altro processo. Lo stub con l'oggetto di applicazione si trova e comunica con un proxy corrispondente disponibile con il client che lo chiama. Vedere anche proxy.  
  
 nodo secondario  
 Vedere figlio.  
  
 operazione sincrona  
 Operazione avviata dal codice che viene completato prima che venga avviato l'operazione successiva. Vedere anche l'operazione asincrona.  
  
## <a name="t-z"></a>T-Z  
 Tree  
 Struttura che rappresenta una relazione gerarchica tra gli elementi (nodi). È presente un nodo al livello superiore di una struttura ad albero (radice). Sotto la radice, possono essere presenti più figli. Ogni elemento figlio a sua volta potrebbe essere l'elemento padre di altri elementi figlio, pertanto la diramazione come una struttura ad albero. Una cartella contenente i documenti e altre cartelle è un esempio tipico di una struttura ad albero. Vedere anche gerarchia, nodo, radice, figlio, padre.  
  
 Server Web  
 Un computer che fornisce i servizi Web e le pagine per utenti di Internet e intranet.
