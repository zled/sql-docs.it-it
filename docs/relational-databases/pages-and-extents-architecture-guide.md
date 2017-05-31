---
title: Guida sull&quot;architettura di pagina ed extent | Microsoft Docs
ms.custom: 
ms.date: 10/21/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- page and extent architecture guide
- guide, page and extent architecture
ms.assetid: 83a4aa90-1c10-4de6-956b-7c3cd464c2d2
caps.latest.revision: 2
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 970981a0f8db1baa802a68ea1186211f031488e6
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="pages-and-extents-architecture-guide"></a>Guida sull'architettura di pagina ed extent
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

La pagine è l'unità di base per l'archiviazione dei dati in SQL Server. Un extent è una raccolta di otto pagine fisicamente contigue. Gli extent aiutano a gestire le pagine in modo efficace. Questa guida descrive le strutture dei dati usate per gestire pagine ed extent in tutte le versioni di SQL Server. La comprensione dell'architettura delle pagine e degli extent è importante per la progettazione e lo sviluppo di database efficienti.

## <a name="pages-and-extents"></a>Pagine ed extent

L'unità di base per l'archiviazione dei dati in SQL Server è la pagina. Lo spazio su disco allocato in un file di dati (con estensione mdf o ndf) di un database viene suddiviso logicamente in pagine numerate in modo sequenziale da 0 a n. Le operazioni di I/O su disco vengono eseguite al livello della pagina. Questo significa che SQL Server legge o scrive pagine di dati intere.

Gli extent sono un gruppo di otto pagine fisicamente contigue e vengono utilizzati per gestire in maniera efficiente le pagine. Tutte le pagine sono archiviate in extent.

### <a name="pages"></a>Pagine

In SQL Server la dimensione di una pagina è 8 KB. I database di SQL Server includono pertanto 128 pagine per megabyte. Ogni pagina inizia con un'intestazione di 96 byte utilizzata per archiviare informazioni di sistema relative alla pagina. Queste informazioni includono il numero della pagina, il tipo di pagina, la quantità di spazio disponibile nella pagina e l'ID dell'unità di allocazione dell'oggetto proprietario della pagina.

Nella tabella seguente vengono elencati i tipi di pagina usati nei file di dati di un database SQL Server.

|Tipo di pagina | Sommario |
|-------|-------|
|Dati |Righe di dati con tutti i dati, ad eccezione di dati text, ntext, image, nvarchar (max), varchar (max), varbinary (max) e xml, quando il testo nella riga è impostato su ON. |
|Indice |Voci di indice. |
|Test/Image |Tipi di dati Large Object: (text, ntext, image, nvarchar(max), varchar(max), varbinary(max) e dati xml) <br> Colonne a lunghezza variabile quando la riga di dati supera 8 KB: (varchar, nvarchar, varbinary e sql_variant) |
|Mappa di allocazione globale (GAM, Global Allocation Map), Mappa di allocazione globale condivisa (SGAM, Shared Global Allocation Map) |Informazioni che indicano se gli extent sono allocati. |
|Spazio libero nella pagina (PFS, Page Free Space) |Informazioni sull'allocazione delle pagine e sullo spazio disponibile nelle pagine. |
|Index Allocation Map |Informazioni sugli extent utilizzati da una tabella o da un indice per unità di allocazione. |
|Mappa delle modifiche di copia bulk (BCM, Bulk Changed Map) |Informazioni sugli extent modificati da operazioni bulk eseguite dopo l'ultima istruzione BACKUP LOG per unità di allocazione. |
|Mappa differenziale delle modifiche (DCM, Differential Changed Map) |Informazioni sugli extent modificati dopo l'esecuzione dell'ultima istruzione BACKUP DATABASE. |

> [!NOTE]
> I file di log non includono pagine, ma solo una serie di record di log.

Le righe di dati vengono inserite in sequenza nella pagina iniziando immediatamente dopo l'intestazione. Una tabella dell'offset delle righe inizia alla fine della pagina. Ogni tabella dell'offset delle righe include una voce per ogni riga della pagina e in ogni voce viene registrata la distanza del primo byte della riga dall'inizio della pagina. Le voci della tabella dell'offset delle righe sono in sequenza inversa rispetto a quella delle righe della pagina.

![page_architecture](../relational-databases/media/page-architecture.gif)

**Supporto per righe di grandi dimensioni**  

Le righe non possono estendersi su più pagine. È tuttavia possibile che parti di una riga vengano spostate all'esterno della pagina della riga in modo che questa possa di fatto essere di grandi dimensioni. La quantità massima di dati e overhead contenuti in una singola riga di una pagina è 8.060 byte (8 KB). Questa limitazione non include tuttavia i dati archiviati nel tipo di pagina Text/Image. Questa restrizione è assoluta per tabelle contenenti colonne di tipo varchar, nvarchar, varbinary o sql_variant. Quando la dimensione totale delle righe di tutte le colonne a lunghezza fissa e variabile di una tabella supera il limite di 8.060 byte, SQL Server sposta dinamicamente una o più colonne a lunghezza variabile all'interno di pagine nell'unità di allocazione ROW_OVERFLOW_DATA, iniziando dalla colonna con la larghezza maggiore. Questa operazione viene eseguita ogni volta che un aggiornamento o un inserimento aumenta la dimensione totale della riga fino a superare il limite di 8.060 byte. Quando una colonna viene spostata in una pagina nell'unità di allocazione ROW_OVERFLOW_DATA, viene mantenuto un puntatore di 24 byte sulla pagina originale nell'unità di allocazione IN_ROW_DATA. Se un'operazione successiva riduce la dimensione della riga, SQL Server sposta nuovamente le colonne nella pagina di dati originale in maniera dinamica. 


### <a name="extents"></a>Extents 

L'extent è l'unità di base in cui viene gestito lo spazio. Un extent è costituito da otto pagine fisicamente contigue, ovvero da 64 KB. I database di SQL Server includono pertanto 16 extent per megabyte.

Per allocare lo spazio con la massima efficienza, in SQL Server non vengono allocati interi extent in tabelle che includono quantità di dati ridotte. SQL Server include due tipi di extent: 

* Gli extent uniformi sono di proprietà di un unico oggetto, pertanto le otto pagine dell'extent possono essere utilizzate solo da tale oggetto.
* Gli extent misti possono essere condivisi al massimo da otto oggetti. Ognuna delle otto pagine dell'extent può essere di proprietà di un oggetto differente.


In una nuova tabella o nuovo indice vengono generalmente allocate pagine da extent misti. Se la tabella o l'indice aumenta di dimensioni fino a includere otto pagine, per le allocazioni successive a esso dirette vengono utilizzati extent uniformi. Se si crea un indice per una tabella esistente che contiene un numero di righe sufficiente per generare otto pagine nell'indice, tutte le allocazioni per l'indice appartengono a extent uniformi.

![Extents](../relational-databases/media/extents.gif)

## <a name="managing-extent-allocations-and-free-space"></a>Gestione delle allocazioni di extent e dello spazio libero 

Le strutture di dati di SQL Server che consentono di gestire le allocazioni degli extent e di tenere traccia dello spazio su disco sono organizzate in modo relativamente semplice. Tali strutture offrono i vantaggi seguenti: 

* Le informazioni relative allo spazio libero sono compresse al massimo e occupano pertanto un numero ridotto di pagine.   
  Questa caratteristica comporta un aumento della velocità a causa della riduzione della quantità di letture su disco necessarie per recuperare le informazioni sull'allocazione. In questo modo, aumenta inoltre la probabilità che le pagine di allocazione vengano mantenute nella memoria e non richiedano ulteriori letture. 

* La maggior parte delle informazioni relative all'allocazione non è concatenata. Questo aspetto semplifica la gestione delle informazioni sull'allocazione.    
  Ogni allocazione o deallocazione di pagina può essere eseguita in modo rapido. Questa caratteristica riduce la contesa tra attività simultanee di allocazione o deallocazione di pagine. 

### <a name="managing-extent-allocations"></a>Gestione delle allocazioni di extent

In SQL Server vengono utilizzati due tipi di mappe per la registrazione delle allocazioni degli extent: 

* Mappa di allocazione globale (GAM, Global Allocation Map)   
  Nelle pagine GAM vengono registrati gli extent allocati. In ogni pagina GAM possono essere registrati riferimenti a 64.000 extent, ovvero a circa 4 GB di dati. La pagina GAM include un bit per ogni extent dell'intervallo che la riguarda. Se il bit è 1, l'extent è disponibile, mentre se è 0, l'extent è allocato. 

* Mappa di allocazione globale condivisa (SGAM, Shared Global Allocation Map)   
  Nelle pagine SGAM vengono registrate informazioni sugli extent misti con almeno una pagina inutilizzata. In ogni pagina SGAM possono essere registrati riferimenti a 64.000 extent, ovvero a circa 4 GB di dati. La pagina SGAM include un bit per ogni extent dell'intervallo che la riguarda. Se il bit è 1, l'extent viene utilizzato come extent misto e include una pagina disponibile. Se il bit è 0, l'extent non viene utilizzato come extent misto o rappresenta un extent misto di cui sono in uso tutte le pagine. 

Nelle pagine GAM e SGAM per ogni extent sono impostati gli schemi di bit indicati di seguito, in base all'utilizzo corrente dell'extent. 

|Utilizzo corrente dell'extent | Impostazione del bit nella pagina GAM | Impostazione del bit nella pagina SGAM |
|---------|----------|------| 
|Disponibile, non utilizzato |1 |0 |
|Extent uniforme oppure extent misto senza spazio libero |0 |0 |
|Extent misto con pagine disponibili |0 |1 |
 
Ciò consente di utilizzare semplici algoritmi di gestione degli extent. Per allocare un extent uniforme, il motore di database cerca un bit 1 nella pagina GAM e lo imposta su 0. Per cercare un extent misto con pagine libere, il motore di database cerca un bit 1 nella pagina SGAM. Per allocare un extent misto, il motore di database cerca un bit 1 nella pagina GAM, lo imposta su 0 e quindi imposta su 1 anche il bit corrispondente nella pagina SGAM. Per deallocare un extent, il motore di database verifica che il bit GAM sia impostato su 1 e il bit SGAM su 0. Gli algoritmi effettivamente usati internamente dal motore di database sono più sofisticati rispetto a quanto descritto in questo argomento, poiché il motore di database distribuisce dati in un database in modo uniforme. Anche gli algoritmi reali, tuttavia, risultano semplificati, in quanto non devono gestire catene di informazioni sull'allocazione degli extent.

### <a name="tracking-free-space"></a>Rilevamento dello spazio libero

Le pagine PFS (Page Free Space, Spazio libero nella pagina) consentono di rilevare lo stato di allocazione di ogni pagina, se una singola pagina sia stata allocata e la quantità di spazio libero in ogni pagina. PFS include un bit per ogni pagina, indicando se la pagina è allocata e, in tal caso, se si tratta di una pagina vuota, in uso dall'1% al 50%, dal 51% all'80%, dall'81% al 95% o dal 96% al 100%.

Dopo che un extent è stato allocato a un oggetto, il motore di database usa le pagine PFS per registrare le pagine dell'extent allocate e quelle disponibili. Queste informazioni vengono usate quando il motore di database deve allocare una nuova pagina. La quantità di spazio libero in una pagina viene mantenuta solo per le pagine heap e text/image. Questo spazio viene usato quando il motore di database deve trovare una pagina con spazio libero disponibile per includere una nuova riga inserita. Per gli indici non è necessario tenere traccia dello spazio libero nella pagina, in quanto il punto di inserimento di una nuova riga viene impostato dai valori delle chiavi di indice.

La prima pagina dopo la pagina dell'intestazione di un file di dati (con il numero di pagina 1) è una pagina PFS. Questa pagina è seguita da una pagina GAM (con il numero di pagina 2) e quindi da una pagina SGAM (pagina 3). È presente una pagina PFS circa 8.000 pagine dopo la prima. È presente un'altra pagina GAM 64.000 extent dopo la prima pagina GAM a pagina 2 e un'altra pagina SGAM 64.000 extent dopo la prima pagina SGAM a pagina 3. Nella figura seguente viene illustrata la sequenza di pagine usata da il motore di database per allocare e gestire gli extent.

![manage_extents](../relational-databases/media/manage-extents.gif)

## <a name="managing-space-used-by-objects"></a>Gestione dello spazio utilizzato dagli oggetti 

Una pagina della mappa di allocazione degli indici (IAM) esegue il mapping degli extent in una parte da 4 gigabyte (GB) di un file di database utilizzato da un'unità di allocazione. Le unità di allocazione possono essere di tre tipi:

* IN_ROW_DATA   
    Contiene una partizione di un heap o di un indice.

* LOB_DATA   
   Contiene tipi di dati Large Object (LOB), ad esempio xml, varbinary (max) e varchar (max).

* ROW_OVERFLOW_DATA   
   Contiene dati a lunghezza variabile archiviati in colonne varchar, nvarchar, varbinary o sql_variant che superano il limite della lunghezza di riga di 8.060 byte. 

Ogni partizione di un heap o di un indice contiene almeno un'unità di allocazione IN_ROW_DATA. Può inoltre contenere un'unità di allocazione LOB_DATA o ROW_OVERFLOW_DATA, a seconda dello schema dell'heap o dell'indice. Per altre informazioni sulle unità di allocazione, vedere Organizzazione di tabelle e indici.

Una pagina IAM include informazioni relative a un intervallo di 4 GB di un file, che corrisponde a quello di una pagina GAM o SGAM. Se l'unità di allocazione contiene extent derivati da più file o più intervalli di 4 GB di un file, saranno presenti più pagine IAM concatenate in una catena IAM. A ogni unità di allocazione corrisponde pertanto almeno una pagina IAM per ogni file in cui sono inclusi extent per l'unità di allocazione. Le pagine IAM per un file possono inoltre essere più di una se il numero di extent del file allocati all'unità di allocazione è maggiore del numero di extent che una pagina IAM è in grado di registrare. 

![iam_pages](../relational-databases/media/iam-pages.gif)

Le pagine IAM vengono allocate per ogni unità di allocazione in base alle necessità e vengono posizionate in modo casuale nel file. La vista di sistema sys.system_internals_allocation_units punta alla prima pagina IAM relativa a un'unità di allocazione. e tutte le pagine IAM di tale unità di allocazione sono concatenate.

> [!IMPORTANT]
> La vista di sistema sys.system_internals_allocation_units è solo per uso interno ed è soggetta a modifiche. Non è garantita la compatibilità.

![iam_chain](../relational-databases/media/iam-chain.gif)
 
Pagine IAM collegate in catena per unità di allocazione Ogni pagina IAM include un'intestazione che indica l'extent iniziale dell'intervallo di extent sul quale viene eseguito il mapping dalla pagina IAM. La pagina IAM include inoltre una mappa di bit di grandi dimensioni in cui ogni bit rappresenta un extent. Il primo bit della mappa rappresenta il primo extent dell'intervallo, il secondo bit rappresenta il secondo extent e così via. Se un bit è 0, significa che l'extent che rappresenta non è allocato all'unità di allocazione proprietaria della pagina IAM. Se il bit è 1, significa che l'extent che rappresenta è allocato all'unità di allocazione proprietaria della pagina IAM.

Se nel motore di database di SQL Server è necessario inserire una nuova riga ma lo spazio libero nella pagina non è sufficiente, vengono usate le pagine IAM e PFS per trovare una pagina per l'allocazione o, nel caso di un heap o di una pagina di tipo text/image, una pagina in cui sia disponibile spazio sufficiente per la riga da inserire. Il motore di database usa le pagine IAM per trovare gli extent allocati all'unità di allocazione. Per ogni extent, il motore di database cerca le pagine PFS per verificare se esiste una pagina da usare. Poiché ogni pagina IAM e PFS include i dati di un numero di pagine elevato, il numero di pagine IAM e PFS di un database è ridotto. Ciò significa che le pagine IAM e PFS in genere risiedono nella memoria del pool di buffer di SQL Server e che pertanto è possibile eseguire rapidamente ricerche al loro interno. Per gli indici, il punto di inserimento di una nuova riga viene impostato dalla chiave dell'indice. In questo caso, il processo di ricerca illustrato in precedenza non viene eseguito.

In motore di database viene allocato un nuovo extent a un'unità di allocazione solo se non viene trovata rapidamente una pagina di un extent esistente in cui sia disponibile spazio sufficiente per la riga da inserire. Nel motore di database, gli extent da allocare vengono selezionati tra quelli disponibili nel filegroup usando un algoritmo di allocazione proporzionale. Se un filegroup include due file, in uno dei quali lo spazio libero è doppio rispetto all'altro, verranno allocate due pagine del file che include la quantità di spazio libero maggiore per ogni pagina allocata dell'altro file. Ciò significa che la percentuale di spazio utilizzato deve essere analoga in tutti i file di un filegroup. 

 
## <a name="tracking-modified-extents"></a>Rilevamento degli extent modificati 

SQL Server usa due strutture di dati interne per rilevare gli extent modificati tramite operazioni di copia bulk e di quelli modificati successivamente al backup completo più recente. Queste strutture di dati consentono di accelerare in misura significativa le operazioni di backup differenziale. Esse accelerano inoltre la registrazione delle operazioni di copia bulk con database per i quali viene utilizzato il modello di recupero con registrazione minima delle operazioni bulk. Come le pagine mappa di allocazione globale (GAM, Global Allocation Map) e mappa di allocazione globale condivisa (SGAM, Shared Global Allocation Map), queste strutture sono mappe di bit in cui ogni bit rappresenta un singolo extent. 

* Mappa differenziale delle modifiche (DCM, Differential Changed Map)   
   Rileva gli extent modificati dopo l'esecuzione dell'ultima istruzione BACKUP DATABASE. Se il bit di un extent è 1, l'extent è stato modificato dopo l'esecuzione dell'ultima istruzione BACKUP DATABASE. Se invece è 0, l'extent non è stato modificato. Durante il backup differenziale vengono lette solo le pagine DCM per identificare gli extent modificati. In questo modo, il numero di pagine di cui è necessario eseguire l'analisi durante il backup differenziale risulta notevolmente ridotto. La durata dell'esecuzione di un backup differenziale è proporzionale al numero di extent modificati dopo l'esecuzione dell'ultima istruzione BACKUP DATABASE e non alle dimensioni complessive del database. 

* Mappa delle modifiche di copia bulk (BCM, Bulk Changed Map)   
   Rileva gli extent modificati mediante operazioni con registrazione minima delle operazioni bulk dall'esecuzione dell'ultima istruzione BACKUP LOG. Se il bit di un extent è 1, l'extent è stato modificato mediante un'operazione con registrazione minima delle operazioni bulk dall'esecuzione dell'ultima istruzione BACKUP LOG. Se invece è 0, l'extent non è stato modificato mediante operazioni con registrazione minima delle operazioni bulk. Sebbene le pagine BCM siano presenti in tutti i database, esse risultano utili solo se il database utilizza il modello di recupero con registrazione minima delle operazioni bulk. Grazie a tale modello, quando viene eseguita un'istruzione BACKUP LOG il processo di backup esegue l'analisi delle pagine BCM per identificare gli extent che sono stati modificati, quindi li include nel backup del log. In questo modo, se il database viene ripristinato da un backup di database e da una sequenza di backup del log delle transazioni, viene eseguito il recupero delle operazioni con registrazione minima delle operazioni bulk. Le pagine BCM non risultano utili in database che utilizzano il modello di recupero con registrazione minima in quanto non prevede la registrazione delle operazioni con registrazione minima delle operazioni bulk, né in database che utilizzano il modello di recupero con registrazione completa in quanto, con questo modello, le operazioni con registrazione minima delle operazioni bulk vengono considerate come operazioni con registrazione completa delle operazioni bulk. 

L'intervallo tra le pagine DCM e BCM corrisponde all'intervallo tra le pagine GAM e SGAM, ovvero 64.000 extent. All'interno di un file fisico le pagine DCM e BCM sono seguite dalle pagine GAM e SGAM:

![special_page_order](../relational-databases/media/special-page-order.gif)
 

