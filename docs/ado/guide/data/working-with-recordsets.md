---
title: Utilizzo di recordset | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recordset object [ADO]
ms.assetid: bdf9a56a-de4a-44de-9111-2f11ab7b16ea
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 368e3b3a793bce6b6182ba262493d9a8ed1ac1bd
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="working-with-recordsets"></a>Utilizzo di recordset
Il **Recordset** oggetto dispone di funzionalità incorporate che consentono ridisporre l'ordine dei dati nel set di risultati, per cercare un record specifico in base a criteri specificati e anche per ottimizzare le operazioni di ricerca tramite gli indici. Se queste funzionalità sono disponibili per l'uso dipende dal provider e in alcuni casi, ad esempio quelle del [indice](../../../ado/reference/ado-api/index-property.md) proprietà, ovvero la struttura dell'origine dati stessa.  
  
## <a name="arranging-data"></a>Disposizione dei dati  
 Spesso il modo più efficiente per ordinare i dati del **Recordset** specificando una clausola ORDER BY nel comando SQL utilizzato per restituire risultati. Tuttavia, potrebbe essere necessario modificare l'ordine dei dati in un **Recordset** che è già stato creato. È possibile utilizzare il **ordinamento** proprietà per definire l'ordine in cui le righe di un **Recordset** vengono scorsi. Inoltre, il **filtro** proprietà determina quali righe sono accessibili quando si attraversano righe.  
  
 Il **ordinamento** proprietà imposta o restituisce un **stringa** i nomi di valore che indica il campo nel **Recordset** di ordinamento. Ogni nome è separato da una virgola e, facoltativamente, è seguita da uno spazio e la parola chiave **ASC** (Ordina il campo in ordine crescente) o **DESC** (Ordina il campo in ordine decrescente). Per impostazione predefinita, se è specificata alcuna parola chiave, il campo viene ordinato in ordine crescente.  
  
 L'operazione di ordinamento è efficiente poiché i dati non è fisicamente ordinati, sono possibile accedere nell'ordine specificato da un indice.  
  
 Il **ordinamento** proprietà richiede la [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà da impostare **adUseClient**. Verrà creato un indice temporaneo per ogni campo specificato nella **ordinamento** proprietà se non ne esiste già.  
  
 L'impostazione di **ordinamento** proprietà in una stringa vuota verrà reimpostato le righe in base all'ordine originale e verranno eliminati gli indici temporanei. Gli indici esistenti non verranno eliminati.  
  
 Si supponga che un **Recordset** contiene tre campi denominati *firstName*, *middleInitial*, e *lastName*. Impostare il **ordinamento** proprietà nella stringa di "`lastName DESC, firstName ASC`", verrà ordine con cui il **Recordset** in base al cognome in ordine decrescente e quindi in base al nome in ordine crescente. Il secondo nome viene ignorato.  
  
 Nessun campo di cui viene fatto riferimento in una stringa di criteri di ordinamento può essere denominato "ASC" o "DESC" in quanto tali nomi in conflitto con le parole chiave **ASC** e **DESC**. Assegnare a un campo che dispone di un alias di un nome in conflitto con il **AS** (parola chiave) nella query che restituisce il **Recordset**.  
  
 Per ulteriori informazioni su **Recordset** filtro, vedere "Filtro dei risultati" più avanti in questo argomento.  
  
## <a name="finding-a-specific-record"></a>Ricerca di un Record specifico  
 ADO.NET fornisce il [trovare](../../../ado/reference/ado-api/find-method-ado.md) e [Seek](../../../ado/reference/ado-api/seek-method.md) metodi per l'individuazione di un record specifico in un **Recordset**. Il **trovare** metodo è supportato da numerosi provider ma è limitato a un unico criterio di ricerca. Il **Seek** metodo supporta la ricerca a più criteri, ma non è supportato da tutti i provider.  
  
 Gli indici nei campi possono migliorare notevolmente le prestazioni del **trovare** (metodo) e **ordinamento** e **filtro** le proprietà del **Recordset** oggetto. È possibile creare un indice interno per un **campo** oggetto impostando la relativa proprietà dinamica [Ottimizza](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) proprietà. Questa proprietà dinamica viene aggiunta per il **proprietà** insieme del **campo** oggetto quando si imposta la [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà **adUseClient**. Tenere presente che l'indice è interno in ADO, è possibile accedervi o utilizzarlo per altri scopi. Inoltre, l'indice è diverso da quello di [indice](../../../ado/reference/ado-api/index-property.md) proprietà del **Recordset** oggetto.  
  
 Il **trovare** metodo individua rapidamente un valore all'interno di una colonna (campo) di un **Recordset**. È spesso possibile migliorare la velocità del **trovare** metodo su una colonna utilizzando il **Ottimizza** proprietà per creare un indice su di esso.  
  
 Il **trovare** metodo limita la ricerca per il contenuto di un campo. Il **Seek** metodo presuppone che si dispone di un indice e altre limitazioni. Se è necessario eseguire la ricerca di più campi che non sono la base di un indice o se il provider non supporta gli indici, è possibile limitare i risultati utilizzando il **filtro** proprietà del **Recordset** oggetto.  
  
### <a name="find"></a>Trova  
 Il **trovare** metodo cerca un **Recordset** per la riga che soddisfa il criterio specificato. Facoltativamente, la direzione della ricerca, la riga iniziale e offset dalla riga iniziale può essere specificata. Se viene soddisfatto il criterio, la posizione della riga corrente è impostata su record trovato. in caso contrario, la posizione viene impostata per la fine o inizio del **Recordset**, a seconda della direzione di ricerca.  
  
 Per il criterio, è possibile specificare solo un nome di colonna singola. In altre parole, questo metodo non supporta ricerche più colonne.  
  
 L'operatore di confronto per il criterio può essere"**>**"(maggiore di),"**\<**" (minore di), "=" (uguale), "> =" (maggiore o uguale a), "< =" (minore o uguale a), " <> "(non uguale), o"LIKE"(criteri di ricerca).  
  
 Il valore di criterio può essere una stringa, un numero a virgola mobile o una data. I valori stringa sono delimitati da virgolette singole o virgolette "#" (simbolo di cancelletto) (ad esempio, "stato = 'WA'" o "stato = WA # #"). I valori di data vengono delimitati da virgolette "#" (simbolo di cancelletto) (ad esempio, "start_date > # #7/22/97").  
  
 Se l'operatore di confronto è "mi piace", il valore di stringa può contenere un asterisco (*) per trovare una o più occorrenze di qualsiasi carattere o una sottostringa. Ad esempio, "stato come sto\*'" corrisponde a Milano e Massachusetts. Inoltre, è possibile utilizzare asterischi iniziali e finali per trovare una sottostringa all'interno di valori. Ad esempio, "stato ad esempio '\*come\*'" corrisponde Alaska, Arkansas e Massachusetts.  
  
 Asterischi possono essere utilizzati solo alla fine di una stringa di criteri o insieme all'inizio e fine di una stringa di criteri, come illustrato in precedenza. È possibile usare l'asterisco come carattere jolly iniziale ('* str') o incorporati con caratteri jolly s\*r'). Ciò genererà un errore.  
  
### <a name="seek-and-index"></a>Ricerca e indice  
 Utilizzare il **Seek** metodo insieme con il **indice** proprietà se il provider sottostante supporta gli indici per il **Recordset** oggetto. Utilizzare il [supporta](../../../ado/reference/ado-api/supports-method.md)**(adSeek)** metodo per determinare se il provider sottostante supporta **Seek**e **Supports (adIndex)** metodo per determinare se il provider supporta gli indici. (Ad esempio, il [il Provider OLE DB per Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) supporta **Seek** e **indice**.)  
  
 Se **Seek** non trovare la riga desiderata, nessun errore si verifica e la riga è posizionato alla fine del **Recordset**. Impostare il **indice** proprietà per l'indice desiderato prima dell'esecuzione di questo metodo.  
  
 Questo metodo è supportato solo con i cursori sul lato server. Ricerca non è supportata quando il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) valore della proprietà di **Recordset** oggetto è **adUseClient**.  
  
 Questo metodo può essere utilizzato solo quando il **Recordset** oggetto è stato aperto con un [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valore **adCmdTableDirect**.  
  
## <a name="filtering-the-results"></a>Filtrare i risultati  
 Il **trovare** metodo limita la ricerca per il contenuto di un campo. Il **Seek** metodo presuppone che si dispone di un indice e altre limitazioni. Se è necessario eseguire la ricerca di più campi che non sono la base di un indice o se il provider non supporta gli indici, è possibile limitare i risultati utilizzando il **filtro** proprietà del **Recordset** oggetto.  
  
 Utilizzare il **filtro** proprietà selettivo i record in un **Recordset** oggetto. Filtrati **Recordset** diventa il cursore corrente, che significa che i record non soddisfa il **filtro** criteri non sono disponibili nel **Recordset** fino a quando il **Filtro** viene rimosso. Altre proprietà che restituiscono valori in base al cursore corrente sono interessate, ad esempio **AbsolutePosition**, **AbsolutePage**, **RecordCount**, e  **PageCount**. Questo è l'impostazione di **filtro** proprietà su un valore specifico sposterà il record corrente al primo record che soddisfa il nuovo valore.  
  
 Il **filtro** proprietà accetta un argomento di tipo variant. Questo valore rappresenta uno dei tre metodi per l'utilizzo di **filtro** proprietà: una stringa di criteri, un **FilterGroupEnum** costante o una matrice di segnalibri. Per ulteriori informazioni, vedere la sezione filtro con una stringa di criteri di filtro con una costante e filtro con i segnalibri più avanti in questo argomento.  
  
> [!NOTE]
>  Quando si conoscono i dati che si desidera selezionare, è in genere più efficiente per aprire un **Recordset** con un'istruzione SQL che filtra il set di risultati, invece di basarsi sul **filtro** proprietà.  
  
 Per rimuovere un filtro da un **Recordset**, utilizzare il **adFilterNone** costante. L'impostazione di **filtro** proprietà in una stringa di lunghezza zero ("") ha lo stesso effetto dell'utilizzo di **adFilterNone** costante.  
  
### <a name="filtering-with-a-criteria-string"></a>Applicazione di filtri con una stringa di criteri  
 La stringa di criteri è costituita da clausole nel formato *nomecampo operatore valore* (ad esempio, `"LastName = 'Smith'"`). È possibile creare clausole composte concatenando clausole singole con **AND** (ad esempio, `"LastName = 'Smith' AND FirstName = 'John'"`) e **o** (ad esempio, `"LastName = 'Smith' OR LastName = 'Jones'"`). Utilizzare le seguenti linee guida per le stringhe di criteri:  
  
-   *FieldName* deve essere un nome di campo valido di **Recordset**. Se il nome del campo contiene spazi, è necessario racchiudere il nome tra parentesi quadre.  
  
-   *Operatore* deve essere uno dei seguenti:  **\<** ,  **>** ,  **\< =** ,  **>=**  ,  **<>** ,  **=** , o **come**.  
  
-   *Valore* è il valore con cui si confronteranno i valori dei campi (ad esempio, `'Smith'`, `#8/24/95#`, `12.345`, o `$50.00`). Utilizzare le virgolette singole (') con le stringhe e caratteri cancelletto (`#`) con le date. Per i numeri, è possibile utilizzare la notazione scientifica, segni di dollaro e decimali. Se *operatore* è **come**, *valore* possono usare caratteri jolly. Solo l'asterisco (\*) e segno di percentuale (%) jolly sono consentiti i caratteri e devono essere l'ultimo carattere nella stringa. *Valore* non può essere null.  
  
    > [!NOTE]
    >  Per includere le virgolette singole (') nel filtro *valore*, utilizzare due virgolette singole per rappresentare uno. Ad esempio, per filtrare *base*, la stringa di criteri deve essere `"col1 = 'O''Malley'"`. Per includere virgolette all'inizio e alla fine del valore del filtro, racchiudere la stringa tra segni di cancelletto (#). Ad esempio, per filtrare *'1'*, la stringa di criteri deve essere `"col1 = #'1'#"`.  
  
 Non vi è alcun precedenza tra **AND** e **o**. Le clausole possono essere raggruppate all'interno delle parentesi. Tuttavia, non è possibile raggruppare clausole unite tramite un **o** e quindi aggiungere il gruppo a un'altra clausola con l'operatore AND, come indicato di seguito.  
  
```  
(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'  
```  
  
 In alternativa, è possibile creare il filtro come indicato di seguito.  
  
```  
(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')  
```  
  
 In un **come** clausola, è possibile utilizzare un carattere jolly all'inizio e alla fine del criterio (ad esempio, `LastName Like '*mit*'`) o solo alla fine del criterio (ad esempio, `LastName Like 'Smit*'`).  
  
### <a name="filtering-with-a-constant"></a>Applicazione di filtri con una costante  
 Le costanti seguenti sono disponibili per il filtro **recordset**.  
  
|Costante|Description|  
|--------------|-----------------|  
|**adFilterAffectedRecords**|I filtri per visualizzare solo i record interessati dall'ultima **eliminare**, **Resync**, **UpdateBatch**, o **CancelBatch** chiamare.|  
|**adFilterConflictingRecords**|Filtri per la visualizzazione di record che non è l'ultimo aggiornamento batch.|  
|**adFilterFetchedRecords**|I filtri per visualizzare i record nella cache corrente, vale a dire i risultati dell'ultima chiamata per recuperare i record dal database.|  
|**adFilterNone**|Rimuove il filtro corrente e ripristina tutti i record per la visualizzazione.|  
|**adFilterPendingRecords**|I filtri per visualizzare solo i record che sono stati modificati ma non sono ancora stati inviati al server. Applicabile solo per la modalità di aggiornamento batch.|  
  
 Le costanti del filtro rendono più semplice risolvere i singoli record conflitti durante la modalità di aggiornamento batch in quanto consente di visualizzare, ad esempio, solo i record che sono stati interessati durante l'ultima **UpdateBatch** chiamata al metodo, come illustrato di esempio seguente.  
  
 `Attribute VB_Name = "modExaminingData"`  
  
### <a name="filtering-with-bookmarks"></a>Applicazione di filtri con segnalibri  
 Infine, è possibile passare una matrice di tipo variant di segnalibri per il **filtro** proprietà. Il cursore risulta conterrà solo i record il cui segnalibro è stato passato alla proprietà. Esempio di codice seguente crea una matrice di segnalibri dai record di un **Recordset** "B" che hanno nel *ProductName* campo. Passa quindi la matrice di **filtro** proprietà consente di visualizzare le informazioni e il valore risultante filtrato **Recordset**.  
  
```  
'BeginFilterBkmk  
Dim vBkmkArray() As Variant  
Dim i As Integer  
  
'Recordset created using "SELECT * FROM Products" as command.  
'So, we will check to see if ProductName has a capital B, and  
'if so, add to the array.  
i = 0  
Do While Not objRs.EOF  
    If InStr(1, objRs("ProductName"), "B") Then  
        ReDim Preserve vBkmkArray(i)  
        vBkmkArray(i) = objRs.Bookmark  
        i = i + 1  
        Debug.Print objRs("ProductName")  
    End If  
    objRs.MoveNext  
Loop  
  
'Filter using the array of bookmarks.  
objRs.Filter = vBkmkArray  
  
objRs.MoveFirst  
Do While Not objRs.EOF  
    Debug.Print objRs("ProductName")  
    objRs.MoveNext  
Loop  
'EndFilterBkmk  
```  
  
## <a name="creating-a-clone-of-a-recordset"></a>Creazione di un Clone di un Recordset  
 Utilizzare il **Clone** duplicato per creare più **Recordset** oggetti, specialmente se si desidera mantenere più di un record corrente in un determinato set di record. Utilizzando il **Clone** è più efficiente rispetto alla creazione e l'apertura di un nuovo metodo **Recordset** oggetto con la stessa definizione originale.  
  
 Il record corrente di un clone appena creato viene originariamente impostato al primo record. Il puntatore del record corrente in un duplicato **Recordset** non è sincronizzato con l'originale o viceversa. È possibile passare in modo indipendente in ogni **Recordset**.  
  
 Le modifiche apportate a uno **Recordset** oggetto sono visibili in tutti i relativi cloni indipendentemente dal tipo di cursore. Tuttavia, dopo l'esecuzione di [Requery](../../../ado/reference/ado-api/requery-method.md) sull'originale **Recordset**, i cloni non saranno sincronizzati all'originale.  
  
 Chiusura originale **Recordset** non chiudere le copie e neppure la chiusura di chiudere una copia originale o una qualsiasi delle altre copie.  
  
 È possibile clonare un **Recordset** oggetto solo se supporta i segnalibri. I valori di segnalibro sono intercambiabili; ovvero, un riferimento di segnalibro da un **Recordset** oggetto fa riferimento allo stesso record in uno dei relativi cloni.

