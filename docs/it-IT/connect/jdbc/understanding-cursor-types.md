---
title: Informazioni sui tipi di cursore | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4f4d3db7-4f76-450d-ab63-141237a4f034
caps.latest.revision: 51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 482b8e18197b7420c254535112f68e3827d8643c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-cursor-types"></a>Informazioni sui tipi di cursore
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Nei database relazionali le operazioni vengono eseguite su set di righe completi. Il set di righe restituito da un'istruzione SELECT include tutte le righe che soddisfano le condizioni specificate nella clausola WHERE dell'istruzione. Il set di righe completo restituito dall'istruzione è noto come set di risultati. Le applicazioni non sono sempre in grado di gestire in modo efficiente un intero set di risultati come singola unità. In tali applicazioni deve essere pertanto disponibile un meccanismo per l'elaborazione di una riga singola o di un blocco di righe di dimensioni ridotte. I cursori sono un'estensione dei set di risultati che implementano appunto tale meccanismo.  
  
 I cursori estendono le funzionalità di elaborazione dei set di risultati nei modi seguenti:  
  
-   Consentono il posizionamento su righe specifiche del set di risultati.  
  
-   Recuperano una riga o un blocco di righe dalla posizione corrente del set di risultati.  
  
-   Supportano le modifiche ai dati della riga in corrispondenza della posizione corrente nel set di risultati.  
  
-   Supportano livelli diversi di visibilità per le modifiche apportate da altri utenti ai dati del database inclusi nel set di risultati.  
  
> [!NOTE]  
>  Per una descrizione completa del [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di cursore, vedere l'argomento "Tipi di cursore (motore di Database)" nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
 La specifica JDBC fornisce supporto per cursori forward-only e scorrevoli sensibili o non sensibili alle modifiche apportate da altri processi e che possono essere di sola lettura o aggiornabili. Questa funzionalità viene fornita per il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe.  
  
## <a name="remarks"></a>Osservazioni  
 Il driver JDBC supporta i tipi di cursore seguenti:  
  
|Set di risultati<br /><br /> risultati (cursore)|Tipo di cursore di SQL Server|Caratteristiche|Proprietà<br /><br /> Metodo|risposta<br /><br /> responseBuffering|Description|  
|------------------------------------|----------------------------|---------------------|-----------------------|----------------------------|-----------------|  
|TYPE_FORWARD_ONLY (CONCUR_READ_ONLY)|N/D|Forward-only, di sola lettura|dirette|completi|L'applicazione deve eseguire una singola iterazione (in avanti) nel set di risultati. Si tratta del comportamento predefinito, corrispondente a un cursore TYPE_SS_DIRECT_FORWARD_ONLY. Tramite il driver viene letto l'intero set di risultati dal server caricandolo in memoria durante l'esecuzione dell'istruzione.|  
|TYPE_FORWARD_ONLY (CONCUR_READ_ONLY)|N/D|Forward-only, di sola lettura|dirette|adaptive|L'applicazione deve eseguire una singola iterazione (in avanti) nel set di risultati. Il comportamento corrisponde a quello di un cursore TYPE_SS_DIRECT_FORWARD_ONLY. Tramite il driver le righe vengono lette dal server quando vengono richieste dall'applicazione, riducendo così al minimo l'utilizzo della memoria sul lato client.|  
|TYPE_FORWARD_ONLY (CONCUR_READ_ONLY)|Fast forward|Forward-only, di sola lettura|cursor|N/D|L'applicazione deve eseguire una singola iterazione (in avanti) nel set di risultati utilizzando un cursore server. Il comportamento è analogo a quello di un cursore TYPE_SS_SERVER_CURSOR_FORWARD_ONLY.<br /><br /> Le righe vengono recuperate dal server in blocchi specificati dalla dimensione di recupero.|  
|TYPE_FORWARD_ONLY (CONCUR_UPDATABLE)|Dinamico (forward-only)|Forward-only, aggiornabile|N/D|N/D|L'applicazione deve eseguire una singola iterazione (in avanti) nel set di risultati per aggiornare una o più righe.<br /><br /> Le righe vengono recuperate dal server in blocchi specificati dalla dimensione di recupero.<br /><br /> Per impostazione predefinita, la dimensione di recupero viene fissata quando l'applicazione chiama il [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.<br /><br /> **Nota:** il driver JDBC fornisce una caratteristica di buffer ADATTIVA che consente di recuperare i risultati di esecuzione di istruzioni dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] quando questi sono necessari l'applicazione, anziché tutti contemporaneamente. Se ad esempio l'applicazione deve recuperare una quantità di dati eccessiva per essere caricata completamente in memoria, il buffer adattivo consente all'applicazione client di recuperare tali dati sotto forma di flusso. Il comportamento predefinito del driver è "**adattivo**". Tuttavia, per ottenere il buffer adattivo per i set di risultati aggiornabili forward-only, l'applicazione deve chiamare in modo esplicito il [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto fornendo un **stringa** valore "**adattivo"**. Per un esempio di codice, vedere [l'aggiornamento di grandi dimensioni campione di dati](../../connect/jdbc/updating-large-data-sample.md).|  
|TYPE_SCROLL_INSENSITIVE|Statico|Scorrevole, non aggiornabile<br /><br /> Gli aggiornamenti, gli inserimenti e le eliminazioni di righe eseguiti esternamente non sono visibili.|N/D|N/D|L'applicazione richiede uno snapshot del database. Il set di risultati non è aggiornabile. È supportato solo CONCUR_READ_ONLY.  Tutti gli altri tipi di concorrenza generano un'eccezione, se utilizzati con questo tipo di cursore.<br /><br /> Le righe vengono recuperate dal server in blocchi specificati dalla dimensione di recupero.|  
|TYPE_SCROLL_SENSITIVE<br /><br /> (CONCUR_READ_ONLY)|Keyset|Scorrevole, sola lettura. Gli aggiornamenti di righe eseguiti esternamente sono visibili e le eliminazioni vengono visualizzate come dati mancanti.<br /><br /> Gli inserimenti di righe eseguiti esternamente non sono visibili.|N/D|N/D|Nell'applicazione devono essere visualizzati i dati modificati solo per le righe esistenti.<br /><br /> Le righe vengono recuperate dal server in blocchi specificati dalla dimensione di recupero.|  
|TYPE_SCROLL_SENSITIVE<br /><br /> (CONCUR_UPDATABLE, CONCUR_SS_SCROLL_LOCKS, CONCUR_SS_OPTIMISTIC_CC, CONCUR_SS_OPTIMISTIC_CCVAL)|Keyset|Scorrevole, aggiornabile<br /><br /> Gli aggiornamenti di righe eseguiti internamente ed esternamente sono visibili e le eliminazioni vengono visualizzate come dati mancanti. Gli inserimenti non sono visibili.|N/D|N/D|L'applicazione può modificare i dati nelle righe esistenti tramite l'oggetto set di risultati. L'applicazione deve inoltre essere in grado di visualizzare le modifiche apportate da altri esternamente all'oggetto set di risultati alle righe.<br /><br /> Le righe vengono recuperate dal server in blocchi specificati dalla dimensione di recupero.|  
|TYPE_SS_DIRECT_FORWARD_ONLY|N/D|Forward-only, di sola lettura|N/D|full o adaptive|Valore intero = 2003. Fornisce un cursore sul lato client di sola lettura completamente memorizzato nel buffer. Non viene creato alcun cursore server.<br /><br /> È supportato solo il tipo di concorrenza CONCUR_READ_ONLY. Tutti gli altri tipi di concorrenza generano un'eccezione, se utilizzati con questo tipo di cursore.|  
|TYPE_SS_SERVER_CURSOR_FORWARD_ONLY|Fast forward|Forward-only|N/D|N/D|Valore intero = 2004. Veloce, con accesso a tutti i dati tramite un cursore server. È aggiornabile quando viene utilizzato con il tipo di concorrenza CONCUR_UPDATABLE.<br /><br /> Le righe vengono recuperate dal server in blocchi specificati dalla dimensione di recupero.<br /><br /> Per ottenere il buffer adattivo per questo caso, l'applicazione deve chiamare in modo esplicito il [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) fornendo un **stringa**  valore "**adattivo"**. Per un esempio di codice, vedere [l'aggiornamento di grandi dimensioni campione di dati](../../connect/jdbc/updating-large-data-sample.md).|  
|TYPE_SS_SCROLL_STATIC|Statico|Gli aggiornamenti di altri utenti non vengono riflessi.|N/D|N/D|Valore intero = 1004. L'applicazione richiede uno snapshot del database. Si tratta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-sinonimo specifico di per il TYPE_SCROLL_INSENSITIVE JDBC e ha lo stesso comportamento di impostazione di concorrenza.<br /><br /> Le righe vengono recuperate dal server in blocchi specificati dalla dimensione di recupero.|  
|TYPE_SS_SCROLL_KEYSET<br /><br /> (CONCUR_READ_ONLY)|Keyset|Scorrevole, sola lettura. Gli aggiornamenti di righe eseguiti esternamente sono visibili e le eliminazioni vengono visualizzate come dati mancanti.<br /><br /> Gli inserimenti di righe eseguiti esternamente non sono visibili.|N/D|N/D|Valore intero = 1005. Nell'applicazione devono essere visualizzati i dati modificati per le righe esistenti. Si tratta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-sinonimo specifico di per il TYPE_SCROLL_SENSITIVE JDBC e ha lo stesso comportamento di impostazione di concorrenza.<br /><br /> Le righe vengono recuperate dal server in blocchi specificati dalla dimensione di recupero.|  
|TYPE_SS_SCROLL_KEYSET<br /><br /> (CONCUR_UPDATABLE, CONCUR_SS_SCROLL_LOCKS, CONCUR_SS_OPTIMISTIC_CC, CONCUR_SS_OPTIMISTIC_CCVAL)|Keyset|Scorrevole, aggiornabile<br /><br /> Gli aggiornamenti di righe eseguiti internamente ed esternamente sono visibili e le eliminazioni vengono visualizzate come dati mancanti. Gli inserimenti non sono visibili.|N/D|N/D|Valore intero = 1005. Nell'applicazione devono essere modificati i dati oppure devono essere visualizzati i dati modificati solo per le righe esistenti. Si tratta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-sinonimo specifico di per il TYPE_SCROLL_SENSITIVE JDBC e ha lo stesso comportamento di impostazione di concorrenza.<br /><br /> Le righe vengono recuperate dal server in blocchi specificati dalla dimensione di recupero.|  
|TYPE_SS_SCROLL_DYNAMIC<br /><br /> (CONCUR_READ_ONLY)|Dynamic|Scorrevole, sola lettura.<br /><br /> Gli aggiornamenti e gli inserimenti di righe eseguiti esternamente sono visibili e le eliminazioni vengono visualizzate come dati mancanti temporanei nel buffer di recupero corrente.|N/D|N/D|Valore intero = 1006. Nell'applicazione devono essere visualizzati i dati modificati per le righe esistenti, nonché le righe inserite ed eliminate nel corso della durata del cursore.<br /><br /> Le righe vengono recuperate dal server in blocchi specificati dalla dimensione di recupero.|  
|TYPE_SS_SCROLL_DYNAMIC<br /><br /> (CONCUR_UPDATABLE, CONCUR_SS_SCROLL_LOCKS, CONCUR_SS_OPTIMISTIC_CC, CONCUR_SS_OPTIMISTIC_CCVAL)|Dynamic|Scorrevole, aggiornabile<br /><br /> Gli aggiornamenti e gli inserimenti di righe eseguiti esternamente e internamente sono visibili e le eliminazioni vengono visualizzate come dati mancanti temporanei nel buffer di recupero corrente.|N/D|N/D|Valore intero = 1006. L'applicazione può modificare i dati per le righe esistenti oppure inserire o eliminare righe tramite l'oggetto set di risultati. L'applicazione deve inoltre essere in grado di visualizzare le modifiche, inserimenti ed eliminazioni apportate da altri esternamente all'oggetto set di risultati.<br /><br /> Le righe vengono recuperate dal server in blocchi specificati dalla dimensione di recupero.|  
  
## <a name="cursor-positioning"></a>Posizionamento dei cursori  
 I cursori TYPE_FORWARD_ONLY, TYPE_SS_DIRECT_FORWARD_ONLY e TYPE_SS_SERVER_CURSOR_FORWARD_ONLY supportano solo il [Avanti](../../connect/jdbc/reference/next-method-sqlserverresultset.md) metodo di posizionamento.  
  
 Il cursore TYPE_SS_SCROLL_DYNAMIC non supporta il [assoluto](../../connect/jdbc/reference/absolute-method-sqlserverresultset.md) e [getRow](../../connect/jdbc/reference/getrow-method-sqlserverresultset.md) metodi. Metodo absolute può essere approssimato da una combinazione di chiamate per il [prima](../../connect/jdbc/reference/first-method-sqlserverresultset.md) e [relativo](../../connect/jdbc/reference/relative-method-sqlserverresultset.md) metodi per i cursori dinamici.  
  
 Il metodo getRow è supportato dai cursori TYPE_FORWARD_ONLY, TYPE_SS_DIRECT_FORWARD_ONLY, TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, TYPE_SS_SCROLL_KEYSET e TYPE_SS_SCROLL_STATIC. I getRow (metodo) con tutti i tipi di cursore forward-only restituisce il numero di righe lette fino a quel momento tramite il cursore.  
  
> [!NOTE]  
>  Quando un'applicazione esegue un di posizionamento del cursore chiamata o una chiamata non supportata per i getRow (metodo), viene generata un'eccezione con il messaggio, "l'operazione richiesta non è supportato con questo tipo di cursore."  
  
 Solo il cursore TYPE_SS_SCROLL_KEYSET e l'equivalente TYPE_SCROLL_SENSITIVE espongono le righe eliminate. Se il cursore è posizionato su una riga eliminata, i valori di colonna non sono disponibili e [rowDeleted](../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md) metodo restituisce "true". Per ottenere\<tipo > metodi generano un'eccezione con il messaggio, "Non è possibile ottenere un valore da una riga eliminata". Le righe eliminate non possono essere aggiornate. Se si tenta di chiamare un aggiornamento\<tipo > metodo in una riga eliminata, viene generata un'eccezione con il messaggio, "non è possibile aggiornare una riga eliminata". Il cursore TYPE_SS_SCROLL_DYNAMIC ha lo stesso comportamento fino a quando non viene tolto dal buffer di recupero corrente.  
  
 I cursori forward e dinamici espongono le righe eliminate in modo simile, ma solo fino a quando rimangono accessibili nel buffer di recupero. Per i cursori forward, questo comportamento è piuttosto lineare. Per i cursori dinamici, si tratta di un comportamento più complesso quando la dimensione di recupero è maggiore di 1. Un'applicazione può spostare il cursore avanti e indietro nella finestra definita dal buffer di recupero, ma la riga eliminata non viene più visualizzata all'uscita dal buffer di recupero originale in cui è stata aggiornata. Se non si desidera che in un'applicazione vengano visualizzate righe eliminate temporanee tramite i cursori dinamici, è necessario utilizzare un'istruzione FETCH RELATIVE con l'argomento 0.  
  
 Se i valori chiave della riga di un cursore TYPE_SS_SCROLL_KEYSET o TYPE_SCROLL_SENSITIVE vengono aggiornati con il cursore, la riga mantiene la propria posizione originale nel set di risultati, indipendentemente dal fatto che la riga aggiornata soddisfi i criteri di selezione del cursore. Se la riga è stata aggiornata all'esterno del cursore, nella posizione originale della riga verrà visualizzata una riga eliminata, ma la riga verrà visualizzata nel cursore solo se nel cursore era presente un'altra riga con i nuovi valori chiave, che tuttavia è stata eliminata.  
  
 Per i cursori dinamici, le righe aggiornate mantengono la posizione all'interno del buffer di recupero fino a quando la finestra definita dal buffer di recupero non viene chiusa. Successivamente, le righe aggiornate possono venire visualizzate in posizioni diverse nel set di risultati o scomparire completamente. Per le applicazioni in cui è necessario evitare le incoerenze temporanee nel set di risultati, è necessario utilizzare una dimensione di recupero pari a 1. L'impostazione predefinita è 8 righe con concorrenza CONCUR_SS_SCROLL_LOCKS e 128 righe con altre concorrenze.  
  
## <a name="cursor-conversion"></a>Conversione dei cursori  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] In alcuni casi è possibile scegliere di implementare un tipo di cursore diverso da quello richiesto, questo comportamento è noto come conversione implicita del cursore (o degradazione del cursore). Per ulteriori informazioni sulla conversione implicita del cursore, vedere l'argomento "Utilizzo della conversione implicita del cursore" nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
 Con [!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)]quando si aggiornano i dati attraverso il risultato ResultSet.TYPE_SCROLL_SENSITIVE e ResultSet.CONCUR_UPDATABLE è impostato, viene generata un'eccezione con un messaggio "il cursore è READ ONLY". Questa eccezione si verifica perché il [!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)] ha eseguito una conversione implicita del cursore per tale risultato set e non ha restituito il cursore aggiornabile è stato richiesto.  
  
 Per ovviare a questo problema, è possibile scegliere una delle due soluzioni seguenti:  
  
-   Verificare che la tabella sottostante disponga di una chiave primaria.  
  
-   Utilizzare [Type_ss_scroll_dynamic](../../connect/jdbc/reference/type-ss-scroll-dynamic-field-sqlserverresultset.md) anziché ResultSet.TYPE_SCROLL_SENSITIVE durante la creazione di un'istruzione.  
  
## <a name="cursor-updating"></a>Aggiornamento dei cursori  
 Gli aggiornamenti sul posto sono supportati per i cursori se la concorrenza e il tipo di cursore supportano gli aggiornamenti. Se il cursore non è posizionato su una riga aggiornabile nel set di risultati (nessuna get\<tipo > chiamata al metodo ha avuto esito positivo), una chiamata a un aggiornamento\<tipo > metodo genererà un'eccezione con il messaggio, "il set di risultati non ha alcuna riga corrente". In base alla specifica JDBC viene generata un'eccezione quando viene chiamato un metodo di aggiornamento per una colonna di un cursore di tipo CONCUR_READ_ONLY. In situazioni in cui la riga non è aggiornabile, ad esempio a causa di un conflitto di concorrenza ottimistica, ad esempio un aggiornamento o eliminazione, l'eccezione potrebbe non venire finché [insertRow](../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md), [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md), o [deleteRow](../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md) viene chiamato.  
  
 Dopo una chiamata per aggiornare\<tipo >, non è possibile accedere alla colonna interessata da get\<tipo > finché updateRow o [cancelRowUpdates](../../connect/jdbc/reference/cancelrowupdates-method-sqlserverresultset.md) è stato chiamato. In questo modo è possibile evitare i problemi che possono verificarsi quando una colonna viene aggiornata utilizzando un tipo diverso da quello restituito dal server e le chiamate al metodo Get successive possono richiamare conversioni del tipo sul lato client che forniscono risultati non accurati. Per ottenere\<tipo > verrà generata un'eccezione con il messaggio "non è possibile accedere colonne aggiornate fino a quando UpdateRow () o cancelRowUpdates () è stato chiamato."  
  
> [!NOTE]  
>  Se il metodo updateRow viene chiamato quando è stata aggiornata alcuna colonna, il driver JDBC genera un'eccezione con il messaggio, "UpdateRow () chiamata quando nessuna colonna è stato aggiornato".  
  
 Dopo aver [moveToInsertRow](../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md) è stato chiamato, verrà generata un'eccezione se qualsiasi metodo diverso da Ottiene\<tipo >, aggiornare\<tipo >, insertRow e dei metodi di posizionamento del cursore (inclusi [ moveToCurrentRow](../../connect/jdbc/reference/movetocurrentrow-method-sqlserverresultset.md)) nel set di risultati viene chiamato. Il metodo moveToInsertRow in modo efficace il set di risultati in modalità di inserimento e metodi di posizionamento del cursore di interrompere la modalità di inserimento. Chiamate di posizionamento relativo del cursore spostano il cursore rispetto alla posizione in che cui si trovava nel prima della chiamata a moveToInsertRow. Dopo le chiamate ai metodi di posizionamento del cursore, la posizione di destinazione finale del cursore diventa la nuova posizione del cursore.  
  
 Se la chiamata effettuata durante l'inserimento non riesce in modalità di posizionamento del cursore, la posizione del cursore dopo la chiamata non riuscita è la posizione del cursore prima moveToInsetRow originale è stata chiamata. Se ha esito negativo insertRow, il cursore rimane nella riga di inserimento e il cursore rimane modalità di inserimento.  
  
 Inizialmente, le colonne nella riga di inserimento hanno uno stato non inizializzato. Le chiamate all'aggiornamento\<tipo > metodo impostato lo stato delle colonne su inizializzato. Una chiamata a get\<tipo > metodo per una colonna non inizializzata genera un'eccezione. Una chiamata al metodo insertRow restituisce tutte le colonne nella riga di inserimento a uno stato non inizializzato.  
  
 Se vi sono colonne non inizializzate quando viene chiamato il metodo insertRow, viene inserito il valore predefinito per la colonna. Se non è disponibile un valore predefinito, ma la colonna ammette i valori Null, viene inserito NULL. Se non è disponibile un valore predefinito e la colonna non ammette i valori Null, il server restituisce un errore e viene generata un'eccezione.  
  
> [!NOTE]  
>  Le chiamate al metodo getRow restituisce 0 in modalità di inserimento.  
>   
>  Il driver JDBC non supporta eliminazioni o aggiornamenti posizionati. In base alla specifica JDBC, il [setCursorName](../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md) metodo non ha alcun effetto e [getCursorName](../../connect/jdbc/reference/getcursorname-method-sqlserverresultset.md) metodo genererà un'eccezione se viene chiamato.  
>   
>  I cursori di sola lettura e statici non sono mai aggiornabili.  
>   
>  In SQL Server i cursori server sono limitati a un singolo set di risultati. Se un batch o una stored procedure contiene più istruzioni, è necessario utilizzare un cursore client di sola lettura forward-only.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei set di risultati con il driver JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  
