---
title: Programmazione di ADO in Visual C++ | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO]
ms.assetid: 11233b96-e05c-4221-9aed-5f20944b0f1c
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8decc959840898d0b82c86c0d955b29a7affddde
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="visual-c-ado-programming"></a>Programmazione di ADO in Visual C++
Il riferimento all'API ADO viene descritta la funzionalità delle ADO application programming interface (API) utilizzando una sintassi simile a Microsoft Visual Basic. Sebbene i destinatari sono tutti gli utenti, i programmatori di ADO utilizzano lingue diverse, ad esempio Visual Basic, Visual C++ (con e senza il **#import** (direttiva)) e Visual J++ (con il pacchetto di classe ADO/WFC).  

> [!NOTE]
> Supporto tecnico Microsoft è terminata per Visual J++ nel 2004.

 Per supportare questa diversità, il [ADO per gli indici di sintassi Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) fornire la sintassi della specifica del linguaggio Visual C++ con collegamenti a descrizioni comune di funzionalità, parametri, comportamenti e così via, nell'API Riferimento.  
  
 ADO viene implementato con le interfacce COM (Component Object Model). Tuttavia, risulta più semplice per i programmatori possono utilizzare COM in alcuni linguaggi di programmazione rispetto ad altri. Ad esempio, quasi tutti i dettagli dell'utilizzo di COM sono gestiti in modo implicito per i programmatori Visual Basic, mentre i programmatori Visual C++ devono occuparsene direttamente.  
  
 Le sezioni seguenti riepilogano i dettagli per i programmatori di C e C++ utilizzando ADO e **#import** direttiva. Si concentra sui tipi di dati specifici di COM (**Variant**, **BSTR**, e **SafeArray**) e la gestione degli errori ( com_error).  
  
## <a name="using-the-import-compiler-directive"></a>Utilizzando la direttiva del compilatore #import  
 Il **#import** direttiva del compilatore Visual C++ semplifica l'utilizzo di ADO metodi e proprietà. La direttiva accetta il nome di un file contenente una libreria dei tipi, ad esempio le DLL di ADO (Msado15.dll) e genera file di intestazione contenenti le dichiarazioni typedef, puntatori intelligenti per le interfacce e le costanti enumerate. Ogni interfaccia incapsulato, o eseguito il wrapping in una classe.  
  
 Per ogni operazione all'interno di una classe (ovvero, una chiamata di metodo o proprietà), non vi è una dichiarazione per chiamare direttamente l'operazione (ovvero, la forma dell'operazione "non elaborata") e una dichiarazione per chiamare l'operazione non elaborato e genera un errore COM se l'operazione non riesce a eseguire succ essfully. Se l'operazione è una proprietà, è in genere una direttiva del compilatore che crea una sintassi alternativa per l'operazione con una sintassi simile a Visual Basic.  
  
 Le operazioni che recuperano il valore di una proprietà hanno il formato dei nomi delle **ottenere***proprietà*. Le operazioni che impostano il valore di una proprietà avere nomi del modulo, **inserire***proprietà*. Le operazioni che impostano il valore di una proprietà con un puntatore a un oggetto ADO hanno nomi di modulo, **PutRef***proprietà*.  
  
 È possibile ottenere o impostare una proprietà con le chiamate delle forme seguenti:  
  
```  
variable = objectPtr->GetProperty(); // get property value   
objectPtr->PutProperty(value);       // set property value  
objectPtr->PutRefProperty(&value);   // set property with object pointer  
```  
  
## <a name="using-property-directives"></a>Proprietà direttive using  
 Il **declspec**  direttiva del compilatore è un'estensione del linguaggio C specifiche di Microsoft che dichiara una funzione usata come una proprietà di una sintassi alternativa. Di conseguenza, è possibile impostare o ottenere valori di una proprietà in modo simile a Visual Basic. Ad esempio, è possibile impostare e ottenere una proprietà in questo modo:  
  
```  
objectPtr->property = value;        // set property value  
variable = objectPtr->property;     // get property value  
```  
  
 Notare che non si dispone di codice:  
  
```  
objectPtr->PutProperty(value);      // set property value  
variable = objectPtr->GetProperty;  // get property value  
```  
  
 Il compilatore genererà appropriata **ottenere***-*, **inserire**-, o **PutRef***proprietà* chiamata in base a sintassi alternativa viene dichiarata e se la proprietà viene letta o scritta.  
  
 Il **declspec**  direttiva del compilatore è possibile dichiarare solo **ottenere**, **inserire**, o **ottenere** e **inserire** sintassi alternativa per una funzione. Operazioni di sola lettura hanno solo un **ottenere** dichiarazione; le operazioni di sola scrittura avere solo un **inserire** dichiarazione; le operazioni che sono di lettura e scrittura hanno entrambi **ottenere** e **inserire** dichiarazioni.  
  
 Solo due dichiarazioni sono possibili con questa direttiva; Tuttavia, ogni proprietà può includere tre funzioni di proprietà: **ottenere***proprietà*, **inserire***proprietà*, e **PutRef**  *Proprietà*. In tal caso, solo due tipi di proprietà presentano la sintassi alternativa.  
  
 Ad esempio, il **comando** oggetto **ActiveConnection** proprietà è dichiarata con una sintassi alternativa per **ottenere***ActiveConnection*e **PutRef***ActiveConnection*. Il **PutRef**-sintassi è consigliabile poiché in pratica, è consigliabile inserire open **connessione** oggetto (vale a dire un **connessione** puntatore all'oggetto) in questo proprietà. D'altra parte, il **Recordset** oggetto ha **ottenere**-, **inserire**-, e **PutRef***ActiveConnection*operazioni, ma nessuna sintassi alternativa.  
  
## <a name="collections-the-getitem-method-and-the-item-property"></a>La proprietà dell'elemento, il metodo GetItem e raccolte  
 ADO definisce le raccolte diverse, tra cui **campi**, **parametri**, **proprietà**, e **errori**. In Visual C++, il **GetItem (***indice***)** metodo restituisce un membro della raccolta. *Indice* è un **Variant**, il cui valore è un indice numerico del membro della raccolta o una stringa contenente il nome del membro.  
  
 Il **declspec**  direttiva del compilatore dichiara il **elemento** della fondamentali proprietà come sintassi alternativa per ogni raccolta **GetItem ()** metodo. La sintassi alternativa utilizza le parentesi quadre ed è simile a un riferimento a una matrice. In generale, le due forme simile al seguente:  
  
```  
  
      collectionPtr->GetItem(index);  
collectionPtr->Item[index];  
```  
  
 Ad esempio, assegnare un valore a un campo di un **Recordset** oggetto, denominato ***rs***, derivata dal **autori** tabella del **pubs** database. Utilizzare il **Item ()** proprietà a cui accedere il terzo **campo** del **Recordset** oggetto **campi** (raccolte sono indicizzate da raccolta uguale a zero; Si supponga che il terzo campo denominato ***au_fname***). Chiamare quindi il **Value ()** metodo sul **campo** oggetto per assegnare un valore stringa.  
  
 Questo può essere espressa in Visual Basic in seguenti quattro modi (gli ultimi due formati sono univoci per Visual Basic; altri linguaggi non dispongono di equivalenti):  
  
```  
rs.Fields.Item(2).Value = "value"  
rs.Fields.Item("au_fname").Value = "value"  
rs(2) = "value"  
rs!au_fname = "value"  
```  
  
 È l'equivalente in Visual C++ per le prime due forme precedente:  
  
```  
rs->Fields->GetItem(long(2))->PutValue("value");   
rs->Fields->GetItem("au_fname")->PutValue("value");  
```  
  
 - oppure - (la sintassi alternativa per il **valore** proprietà viene inoltre visualizzata)  
  
```  
rs->Fields->Item[long(2)]->Value = "value";  
rs->Fields->Item["au_fname"]->Value = "value";  
```  
  
 Per esempi di scorrere una raccolta, vedere la sezione "ADO raccolte" di "Riferimento ADO".  
  
## <a name="com-specific-data-types"></a>Tipi di dati specifici di COM  
 In generale, qualsiasi tipo di dati Visual Basic che trova in riferimento all'API ADO ha un equivalente di Visual C++. Questi includono tipi di dati standard, ad esempio **unsigned char** per un Visual Basic **Byte**, **breve** per **intero**, e  **long** per **lungo**. Cerca in Indexesto la sintassi, vedere esattamente cosa è necessaria per gli operandi di un determinato metodo o proprietà.  
  
 Le eccezioni a questa regola sono i tipi di dati specifici di COM: **Variant**, **BSTR**, e **SafeArray**.  
  
### <a name="variant"></a>Variant  
 Oggetto **Variant** è un tipo di dati strutturati che contiene un valore e un membro di tipo dati. Oggetto **Variant** può contenere un'ampia gamma di altri tipi di dati tra un'altra variante, BSTR, Boolean, puntatore IDispatch o IUnknown, valuta, data e così via. COM fornisce inoltre metodi che semplificano per convertono un tipo di dati in un altro.  
  
 Il **variant_t** incapsula e gestisce il **Variant** tipo di dati.  
  
 Quando il riferimento all'API ADO indica che un metodo o operando di proprietà accetta un valore, significa in genere il valore viene passato un **variant_t**.  
  
 Questa regola è vera in modo esplicito quando il **parametri** sezione negli argomenti di riferimento all'API ADO indica che un operando è un **Variant**. Un'eccezione è rappresentata la documentazione è indicato in modo esplicito dell'operando accetta un tipo di dati standard, ad esempio **lungo** o **Byte**, o un'enumerazione. Un'altra eccezione si verifica quando l'operando assume un **stringa**.  
  
### <a name="bstr"></a>BSTR  
 Oggetto **BSTR** (**B**asic **STR**ing) è un tipo di dati strutturati che contiene una stringa di caratteri e la lunghezza della stringa. COM fornisce i metodi per allocare, modificare e liberare un **BSTR**.  
  
 Il **bstr_t** incapsula e gestisce il **BSTR** tipo di dati.  
  
 Quando il riferimento all'API ADO indica una proprietà o metodo accetta un **stringa** valore, significa che il valore è sotto forma di un **bstr_t**.  
  
### <a name="casting-variantt-and-bstrt-classes"></a>Cast di classi variant_t e bstr_t  
 Non è spesso necessario al codice in modo esplicito un **variant_t** o **bstr_t** in un argomento di un'operazione. Se il **variant_t** o **bstr_t** classe ha un costruttore che corrisponde al tipo di dati dell'argomento, il compilatore genererà appropriata **variant_t** o **bstr_t**.  
  
 Tuttavia, se l'argomento è ambiguo, vale a dire, il tipo di dati dell'argomento corrisponde a più di un costruttore, è necessario eseguire il cast dell'argomento con tipo di dati appropriato per richiamare il costruttore corretto.  
  
 Ad esempio, la dichiarazione per il **Recordset:: Open** metodo:  
  
```  
    HRESULT Open (  
        const _variant_t & Source,  
        const _variant_t & ActiveConnection,  
        enum CursorTypeEnum CursorType,  
        enum LockTypeEnum LockType,  
        long Options );  
```  
  
 Il `ActiveConnection` argomento accetta un riferimento a un **variant_t**, che è possibile codificare una stringa di connessione o un puntatore a un oggetto aperto **connessione** oggetto.  
  
 Il corretto **variant_t** essere costruito in modo implicito se si passa una stringa, ad esempio "`DSN=pubs;uid=MyUserName;pwd=MyPassword;`", o un puntatore, ad esempio "`(IDispatch *) pConn`".  
  
> [!NOTE]
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare **Trusted_Connection = yes** o **Integrated Security = SSPI** anziché l'ID utente e password informazioni nella stringa di connessione.  
  
 Oppure è possibile codificare in modo esplicito un **variant_t** contenente un puntatore, ad esempio "`_variant_t((IDispatch *) pConn, true)`". Il cast, `(IDispatch *)`, risolve l'ambiguità con un altro costruttore che accetta un puntatore a interfaccia IUnknown.  
  
 È fondamentale, sebbene raramente indicato delle tabelle dei fatti che ADO è un'interfaccia IDispatch. Ogni volta che un puntatore a un oggetto ADO deve essere passato come un **Variant**, che è necessario eseguirne il cast come un puntatore a un'interfaccia IDispatch.  
  
 Nell'ultimo caso codice in modo esplicito il secondo argomento booleano del costruttore il valore predefinito facoltativo, `true`. Questo argomento lo induce il **Variant** costruttore da chiamare relativo **AddRef**metodo (), che compensa automaticamente la chiamata ADO la **_variant_t::Release**() (metodo) al termine della chiamata di metodo o proprietà ADO.  
  
### <a name="safearray"></a>SafeArray  
 Oggetto **SafeArray** è un tipo di dati strutturati che contiene una matrice di altri tipi di dati. Oggetto **SafeArray** viene chiamato *provvisoria* perché contiene informazioni relative ai limiti di ciascuna dimensione della matrice e limita l'accesso agli elementi di matrice all'interno di tali limiti.  
  
 Quando il riferimento all'API ADO indica che un metodo o proprietà assume o restituisce una matrice, significa che il metodo o proprietà accetta o restituisce un **SafeArray**, non è una matrice di C/C++ nativa.  
  
 Ad esempio, il secondo parametro del **connessione** oggetto **OpenSchema** metodo richiede una matrice di **Variant** valori. Quelli **Variant** valori devono essere passati come elementi di un **SafeArray**e che **SafeArray** deve essere impostato come valore di un altro **Variant** . Che altri **Variant** che viene passato come secondo argomento di **OpenSchema**.  
  
 Come altri esempi, il primo argomento del **trovare** metodo è un **Variant** il cui valore è una matrice unidimensionale **SafeArray**; ogni prima e seconda argomenti facoltativi di **AddNew** è una matrice unidimensionale **SafeArray**; e il valore restituito di **GetRows** metodo è un **Variant** cui valore è un oggetto bidimensionale **SafeArray**.  
  
## <a name="missing-and-default-parameters"></a>Parametri mancanti e predefiniti  
 Visual Basic consente priva di parametri nei metodi. Ad esempio, il **Recordset** oggetto **aprire** metodo presenta cinque parametri, ma è possibile ignorare i parametri intermedi e omettere quelli finali. Valore predefinito è **BSTR** o **Variant** verrà sostituito in base al tipo di dati dell'operando mancante.  
  
 In C/C++, è necessario specificare tutti gli operandi. Se si desidera specificare un parametro mancante il cui tipo di dati è una stringa, specificare un **bstr_t** contenente una stringa null. Se si desidera specificare un parametro mancante, il cui tipo di dati è un **Variant**, specificare un **variant_t** con un valore DISP_E_PARAMNOTFOUND e tipo VT_ERROR. In alternativa, specificare l'equivalente **variant_t** costante, **vtMissing**, che viene fornito dal **#import** direttiva.  
  
 Tre metodi sono eccezioni per l'utilizzo tipico della **vtMissing**. Questi sono il **Execute** metodi del **connessione** e **comando** oggetti e **NextRecordset** metodo il **Recordset** oggetto. Di seguito sono relative firme:  
  
```  
_RecordsetPtr <A HREF="mdmthcnnexecute.htm">Execute</A>( _bstr_t CommandText, VARIANT * RecordsAffected,   
        long Options );  // Connection  
_RecordsetPtr <A HREF="mdmthcmdexecute.htm">Execute</A>( VARIANT * RecordsAffected, VARIANT * Parameters,   
        long Options );  // Command  
_RecordsetPtr <A HREF="mdmthnextrec.htm">NextRecordset</A>( VARIANT * RecordsAffected );  // Recordset  
```  
  
 I parametri, *RecordsAffected* e *parametri*, sono puntatori a un **Variant**. *I parametri* è un parametro di input che specifica l'indirizzo di un **Variant** contenente un singolo parametro o una matrice di parametri, che verrà modificato il comando in esecuzione. *RecordsAffected* è un parametro di output che specifica l'indirizzo di un **Variant**, in cui viene restituito il numero di righe interessate dal metodo.  
  
 Nel **comando** oggetto **Execute** (metodo), indica che viene specificato alcun parametro impostando *parametri* a uno `&vtMissing` (impostazione consigliata) o a puntatore null (vale a dire **NULL** o zero (0)). Se *parametri* è impostato sul puntatore null, il metodo sostituisce internamente l'equivalente di **vtMissing**e quindi completa l'operazione.  
  
 In tutti i metodi, indicano che il numero di record interessati non deve essere restituito impostando *RecordsAffected* al puntatore null. In questo caso, il puntatore null non è in questo caso è un parametro mancante come indicazione che il metodo deve ignorare il numero di record interessati.  
  
 Di conseguenza, questi tre metodi, è valido per un elemento di codice, ad esempio:  
  
```  
pConnection->Execute("commandText", NULL, adCmdText);   
pCommand->Execute(NULL, NULL, adCmdText);  
pRecordset->NextRecordset(NULL);  
```  
  
## <a name="error-handling"></a>Gestione degli errori  
 In COM, la maggior parte delle operazioni restituisce un codice restituito HRESULT che indica se una funzione è stata completata correttamente. Il **#import** direttiva genera codice wrapper per ogni proprietà o il metodo "non elaborato" e verifica il valore HRESULT restituito. Se il valore HRESULT indica un errore, il codice wrapper genera un errore COM come argomento dal chiamante com_issue_errorex () con il codice restituito HRESULT. Oggetti di errore COM possono essere intercettati in un **provare**-**catch** blocco. (Per i migliori risultati ottenere, intercettare un riferimento a un **com_error** oggetto.)  
  
 Tenere presente che questi sono errori ADO: sono il risultato di errore in un'operazione di ADO. Gli errori restituiti dal provider sottostante vengono visualizzati come **errore** gli oggetti di **connessione** oggetto **errori** insieme.  
  
 Il **#import** direttiva crea solo errori routine di gestione per i metodi e le proprietà dichiarate nella DLL di ADO. Tuttavia, è possibile sfruttare l'errore stesso meccanismo di gestione mediante la scrittura di macro o una funzione inline di controllo degli errori personalizzata. Vedere l'argomento [estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-for-ado.md), o il codice nelle sezioni seguenti per esempi.  
  
## <a name="visual-c-equivalents-of-visual-basic-conventions"></a>Visual C++ gli equivalenti di convenzioni di Visual Basic  
 Di seguito è riportato un riepilogo di alcune convenzioni nella documentazione di ADO, codificate in Visual Basic, nonché i relativi equivalenti in Visual C++.  
  
### <a name="declaring-an-ado-object"></a>Dichiarazione di un oggetto ADO  
 In Visual Basic, una variabile oggetto ADO (in questo caso per un **Recordset** oggetto) è dichiarato come segue:  
  
```  
Dim rst As ADODB.Recordset  
```  
  
 La clausola "`ADODB.Recordset`", è il valore ProgID del **Recordset** dell'oggetto come definito nel Registro di sistema. Una nuova istanza di un **Record** oggetto viene dichiarato come segue:  
  
```  
Dim rst As New ADODB.Recordset  
```  
  
 oppure  
  
```  
Dim rst As ADODB.Recordset  
Set rst = New ADODB.Recordset  
```  
  
 In Visual C++, il **#import** direttiva genera dichiarazioni di tipo puntatore intelligente per tutti gli oggetti ADO. Ad esempio, una variabile che punta a un **recordset** oggetto è di tipo **RecordsetPtr**e viene dichiarata come segue:  
  
```  
_RecordsetPtr  rs;  
```  
  
 Una variabile che punta a una nuova istanza di un **recordset** oggetto viene dichiarato come segue:  
  
```  
_RecordsetPtr  rs("ADODB.Recordset");  
```  
  
 oppure  
  
```  
_RecordsetPtr  rs;  
rs.CreateInstance("ADODB.Recordset");  
```  
  
 oppure  
  
```  
_RecordsetPtr  rs;  
rs.CreateInstance(__uuidof(_Recordset));  
```  
  
 Dopo il **CreateInstance** metodo viene chiamato, la variabile può essere utilizzata come indicato di seguito:  
  
```  
rs->Open(...);  
```  
  
 Si noti che in un caso, il "`.`" operatore viene utilizzato come se la variabile fosse un'istanza di una classe (`rs.CreateInstance`) e in altri casi, il "`->`" operatore viene utilizzato come se la variabile fosse un puntatore a un'interfaccia (`rs->Open`).  
  
 Una variabile può essere utilizzata in due modi perché il "`->`" è l'overload dell'operatore per consentire a un'istanza di una classe si comporta come un puntatore a un'interfaccia. Un membro di classe privata della variabile di istanza contiene un puntatore al **recordset** interfaccia il "`->`" operatore restituisce il puntatore di tipo e il puntatore restituito accede ai membri del **Recordset**  oggetto.  
  
### <a name="coding-a-missing-parameter--string"></a>Codifica di un parametro mancante: stringa  
 Quando è necessario codificare manca un **stringa** operando in Visual Basic, è sufficiente omettere l'operando. In Visual C++, è necessario specificare l'operando. Codice di un **bstr_t** che è una stringa vuota come valore.  
  
```  
_bstr_t strMissing(L"");  
```  
  
### <a name="coding-a-missing-parameter--variant"></a>Codifica di un parametro mancante-Variant  
 Quando è necessario codificare manca un **Variant** operando in Visual Basic, è sufficiente omettere l'operando. In Visual C++, è necessario specificare tutti gli operandi. Codice manca un **Variant** parametro con un **variant_t** impostare il valore speciale, DISP_E_PARAMNOTFOUND e digitare VT_ERROR. In alternativa, specificare **vtMissing**, che viene fornita da una costante predefinita equivalente di **#import** direttiva.  
  
```  
_variant_t  vtMissingYours(DISP_E_PARAMNOTFOUND, VT_ERROR);   
```  
  
 - oppure utilizzare-  
  
```  
...vtMissing...;  
```  
  
### <a name="declaring-a-variant"></a>Dichiarazione di una variabile Variant  
 In Visual Basic, un **Variant** è dichiarato con la **Dim** come segue:  
  
```  
Dim VariableName As Variant  
```  
  
 In Visual C++, dichiarare una variabile come tipo **variant_t**. Schema qualche **variant_t** dichiarazioni illustrate di seguito.  
  
> [!NOTE]
>  Queste dichiarazioni forniscono un'idea approssimativa di ciò che si trattasse del codice in un'applicazione. Per ulteriori informazioni, vedere gli esempi seguenti e la documentazione di Visual C++.  
  
```  
_variant_t  VariableName(value);  
_variant_t  VariableName((data type cast) value);  
_variant_t  VariableName(value, VT_DATATYPE);  
_variant_t  VariableName(interface * value, bool fAddRef = true);  
```  
  
### <a name="using-arrays-of-variants"></a>Utilizzo delle matrici di tipi Variant  
 In Visual Basic, matrici di **varianti** possono essere codificate con il **Dim** istruzione oppure è possibile utilizzare il **matrice** funzione, come illustrato nell'esempio di codice seguente:  
  
```  
Public Sub ArrayOfVariants  
Dim cn As ADODB.Connection  
Dim rs As ADODB.Recordset  
Dim fld As ADODB.Field  
  
    cn.Open "DSN=pubs"  
    rs = cn.OpenSchema(adSchemaColumns, _  
        Array(Empty, Empty, "authors", Empty))  
    For Each fld in rs.Fields  
        Debug.Print "Name = "; fld.Name  
    Next fld  
    rs.Close  
    cn.Close  
End Sub  
```  
  
 Nell'esempio di Visual C++ seguente viene illustrato come utilizzare un **SafeArray** utilizzato con un **variant_t**.  
  
#### <a name="notes"></a>Note  
 Le note seguenti corrispondono alle sezioni commentate nell'esempio di codice.  
  
1.  In questo caso, la funzione inline TESTHR() è definita per sfruttare i vantaggi del meccanismo di gestione degli errori esistente.  
  
2.  È sufficiente una matrice unidimensionale, pertanto è possibile utilizzare **SafeArrayCreateVector**, anziché generici **SAFEARRAYBOUND** dichiarazione e **SafeArrayCreate** funzione. Di seguito è l'aspetto che il codice utilizzando **SafeArrayCreate**:  
  
    ```  
       SAFEARRAYBOUND   sabound[1];  
       sabound[0].lLbound = 0;  
       sabound[0].cElements = 4;  
       pSa = SafeArrayCreate(VT_VARIANT, 1, sabound);  
    ```  
  
3.  Lo schema identificato dalla costante enumerata **adSchemaColumns**, associato a quattro colonne del vincolo: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME e COLUMN_NAME. Pertanto, una matrice di **Variant** valori con quattro elementi viene creato. Il valore di un vincolo che corrisponde alla terza colonna, TABLE_NAME, viene quindi specificato.  
  
     Il **Recordset** restituito è costituito da più colonne, un sottoinsieme di cui le colonne del vincolo. I valori delle colonne per ogni riga restituita devono essere identico per i valori di vincolo corrispondente.  
  
4.  Chi ha familiarità con **SAFEARRAY** può essere sorprendente che **tuttavia**() non viene chiamato prima che l'uscita. In effetti, la chiamata **tuttavia**in questo caso () genererà un'eccezione in fase di esecuzione. Il motivo è che il distruttore per `vtCriteria` chiamerà **VariantClear**() quando il **variant_t** esce dall'ambito, che consente di liberare la **SafeArray**. La chiamata **tuttavia**, senza cancellare manualmente le **variant_t**, determinerebbe il distruttore provare a cancellare un oggetto non valido **SafeArray** puntatore.  
  
     Se **tuttavia** sono stati chiamati, il codice sarebbe simile al seguente:  
  
    ```  
          TESTHR(SafeArrayDestroy(pSa));  
       vtCriteria.vt = VT_EMPTY;  
          vtCriteria.parray = NULL;  
    ```  
  
     Tuttavia, è molto più semplice consentire il **variant_t** gestire il **SafeArray**.  
  
```  
// Visual_CPP_ADO_Prog_1.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
// Note 1  
inline void TESTHR( HRESULT _hr ) {   
   if FAILED(_hr)   
      _com_issue_error(_hr);   
}  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _RecordsetPtr pRs("ADODB.Recordset");  
      _ConnectionPtr pCn("ADODB.Connection");  
      _variant_t vtTableName("authors"), vtCriteria;  
      long ix[1];  
      SAFEARRAY *pSa = NULL;  
  
      pCn->Provider = "sqloledb";  
      pCn->Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);  
      // Note 2, Note 3  
      pSa = SafeArrayCreateVector(VT_VARIANT, 1, 4);  
      if (!pSa)   
         _com_issue_error(E_OUTOFMEMORY);  
  
      // Specify TABLE_NAME in the third array element (index of 2).   
      ix[0] = 2;        
      TESTHR(SafeArrayPutElement(pSa, ix, &vtTableName));  
  
      // There is no Variant constructor for a SafeArray, so manually set the   
      // type (SafeArray of Variant) and value (pointer to a SafeArray).  
  
      vtCriteria.vt = VT_ARRAY | VT_VARIANT;  
      vtCriteria.parray = pSa;  
  
      pRs = pCn->OpenSchema(adSchemaColumns, vtCriteria, vtMissing);  
  
      long limit = pRs->GetFields()->Count;  
      for ( long x = 0 ; x < limit ; x++ )  
         printf( "%d: %s\n", x + 1, ((char*) pRs->GetFields()->Item[x]->Name) );  
      // Note 4  
      pRs->Close();  
      pCn->Close();  
   }  
   catch (_com_error &e) {  
      printf("Error:\n");  
      printf("Code = %08lx\n", e.Error());  
      printf("Code meaning = %s\n", (char*) e.ErrorMessage());  
      printf("Source = %s\n", (char*) e.Source());  
      printf("Description = %s\n", (char*) e.Description());  
   }  
   CoUninitialize();  
}  
```  
  
### <a name="using-property-getputputref"></a>Utilizzando proprietà Get/Put/PutRef  
 In Visual Basic, il nome di una proprietà non è qualificato tramite se viene recuperato, assegnato o assegnare un riferimento.  
  
```  
Public Sub GetPutPutRef  
Dim rs As New ADODB.Recordset  
Dim cn As New ADODB.Connection  
Dim sz as Integer  
cn.Open "Provider=sqloledb;Data Source=yourserver;" & _  
         "Initial Catalog=pubs;Integrated Security=SSPI;"  
rs.PageSize = 10  
sz = rs.PageSize  
rs.ActiveConnection = cn  
rs.Open "authors",,adOpenStatic  
' ...  
rs.Close  
cn.Close  
End Sub  
```  
  
 Questo esempio di Visual C++ viene illustrato il **ottenere**/**inserire**/**PutRef***proprietà*.  
  
#### <a name="notes"></a>Note  
 Le note seguenti corrispondono alle sezioni commentate nell'esempio di codice.  
  
1.  In questo esempio utilizza due forme di un argomento stringa mancante: una costante esplicita, **strMissing**e una stringa che il compilatore utilizzerà per creare una password temporanea **bstr_t** che sarà disponibile per l'ambito del  **Aprire** metodo.  
  
2.  Non è necessario per il cast dell'operando di `rs->PutRefActiveConnection(cn)` a `(IDispatch *)` perché il tipo dell'operando è già `(IDispatch *)`.  
  
```  
// Visual_CPP_ado_prog_2.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr cn("ADODB.Connection");  
      _RecordsetPtr rs("ADODB.Recordset");  
      _bstr_t strMissing(L"");  
      long oldPgSz = 0, newPgSz = 5;  
  
      // Note 1  
      cn->Provider = "sqloledb";  
      cn->Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", strMissing, "", adConnectUnspecified);  
  
      oldPgSz = rs->GetPageSize();  
      // -or-  
      // oldPgSz = rs->PageSize;  
  
      rs->PutPageSize(newPgSz);  
      // -or-  
      // rs->PageSize = newPgSz;  
  
      // Note 2  
      rs->PutRefActiveConnection( cn );  
      rs->Open("authors", vtMissing, adOpenStatic, adLockReadOnly, adCmdTable);  
      printf("Original pagesize = %d, new pagesize = %d\n", oldPgSz, rs->GetPageSize());  
      rs->Close();  
      cn->Close();  
  
   }  
   catch (_com_error &e) {  
      printf("Description = %s\n", (char*) e.Description());  
   }  
   ::CoUninitialize();  
}  
```  
  
### <a name="using-getitemx-and-itemx"></a>Utilizzo di GetItem (x) e l'elemento [x]  
 In questo esempio di Visual Basic viene illustrata la sintassi standard e alternativa per **elemento**().  
  
```  
Public Sub GetItemItem  
Dim rs As New ADODB.Recordset  
Dim name as String  
rs = rs.Open "authors", "DSN=pubs;", adOpenDynamic, _  
         adLockBatchOptimistic, adTable  
name = rs(0)  
' -or-  
name = rs.Fields.Item(0)  
rs(0) = "Test"  
rs.UpdateBatch  
' Restore name  
rs(0) = name  
rs.UpdateBatch  
rs.Close  
End Sub  
```  
  
 In questo esempio di Visual C++ viene **elemento**.  
  
> [!NOTE]
>  La nota seguente corrisponde alle sezioni commentate nell'esempio di codice: quando si accede all'insieme con **elemento**, l'indice, **2**, deve essere impostato **lungo** in modo da un viene richiamato il costruttore appropriato.  
  
```  
// Visual_CPP_ado_prog_3.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
void main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr cn("ADODB.Connection");  
      _RecordsetPtr rs("ADODB.Recordset");  
      _variant_t vtFirstName;  
  
      cn->Provider = "sqloledb";  
      cn->Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", "", "", adConnectUnspecified);  
  
      rs->PutRefActiveConnection( cn );  
      rs->Open("authors", vtMissing, adOpenStatic, adLockOptimistic, adCmdTable);  
      rs->MoveFirst();  
  
      // Note 1. Get a field.  
      vtFirstName = rs->Fields->GetItem((long)2)->GetValue();  
      // -or-  
      vtFirstName = rs->Fields->Item[(long)2]->Value;  
  
      printf( "First name = '%s'\n", (char*)( (_bstr_t)vtFirstName) );  
  
      rs->Fields->GetItem((long)2)->Value = L"TEST";  
      rs->Update(vtMissing, vtMissing);  
  
      // Restore name  
      rs->Fields->GetItem((long)2)->PutValue(vtFirstName);  
      // -or-  
      rs->Fields->GetItem((long)2)->Value = vtFirstName;  
      rs->Update(vtMissing, vtMissing);  
      rs->Close();  
   }  
   catch (_com_error &e) {  
      printf("Description = '%s'\n", (char*) e.Description());  
   }  
   ::CoUninitialize();  
}  
```  
  
### <a name="casting-ado-object-pointers-with-idispatch-"></a>Cast di puntatori a oggetti ADO con (IDispatch *)  
 Viene illustrato come utilizzare il seguente esempio di Visual C++ (IDispatch *) per puntatori a oggetti ADO cast.  
  
#### <a name="notes"></a>Note  
 Le note seguenti corrispondono alle sezioni commentate nell'esempio di codice.  
  
1.  Specificare un oggetto aperto **connessione** oggetto codificato in modo esplicito **Variant**. Eseguire il cast con (IDispatch \*) in modo verrà richiamato il costruttore corretto. Inoltre, impostare in modo esplicito il secondo **variant_t** parametro per il valore predefinito di **true**, pertanto il conteggio dei riferimenti oggetto sarà corretto durante il **Recordset:: Open** Termina l'operazione.  
  
2.  L'espressione, `(_bstr_t)`, non è un cast, ma un **variant_t** operatore che estrae un **bstr_t** stringa dal **Variant** restituito da **valore** .  
  
 L'espressione, `(char*)`, non è un cast, ma un **bstr_t** operatore che estrae un puntatore nella stringa incapsulata in un **bstr_t** oggetto.  
  
 In questa sezione di codice vengono illustrati alcuni dei comportamenti utili degli **variant_t** e **bstr_t** operatori.  
  
```  
// Visual_CPP_ado_prog_4.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr pConn("ADODB.Connection");  
      _RecordsetPtr pRst("ADODB.Recordset");  
  
      pConn->Provider = "sqloledb";  
      pConn->Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);  
  
      // Note 1.  
      pRst->Open("authors", _variant_t((IDispatch *) pConn, true), adOpenStatic, adLockReadOnly, adCmdTable);  
      pRst->MoveLast();  
  
      // Note 2.  
      printf("Last name is '%s %s'\n",   
         (char*) ((_bstr_t) pRst->GetFields()->GetItem("au_fname")->GetValue()),  
         (char*) ((_bstr_t) pRst->Fields->Item["au_lname"]->Value));  
  
      pRst->Close();  
      pConn->Close();  
   }  
   catch (_com_error &e) {  
      printf("Description = '%s'\n", (char*) e.Description());  
   }     
   ::CoUninitialize();  
}  
```
