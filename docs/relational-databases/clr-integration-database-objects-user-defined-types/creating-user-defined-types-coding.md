---
title: Codifica dei tipi definiti dall'utente | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- validation [CLR integration]
- UDTs [CLR integration], coding
- UserDefined serialization format [CLR integration]
- Point UDT
- Parse method
- null values [CLR integration]
- ToString method
- ValidatePoint method
- attributes [CLR integration]
- coding user-defined types [CLR integration]
- Read method
- Write method
- nullability [CLR integration]
- user-defined types [CLR integration], coding
- Currency UDT
- validating UDT values
- exposing UDT properties [CLR integration]
ms.assetid: 1e5b43b3-4971-45ee-a591-3f535e2ac722
caps.latest.revision: 37
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b3a698c63fa5fc7e5a0802716b3112df31cf241f
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35697902"
---
# <a name="creating-user-defined-types---coding"></a>Creazione di tipi definiti dall'utente - la generazione di codice
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Quando si codifica la definizione del tipo definito dall'utente (UDT), è necessario implementare varie caratteristiche a seconda che il tipo UDT venga implementato come classe o come struttura, nonché a seconda delle opzioni di formato e di serializzazione scelte.  
  
 Nell'esempio riportato in questa sezione viene illustrata l'implementazione una **punto** tipo definito dall'utente come una **struct** (oppure **struttura** in Visual Basic). Il **punto** tipo definito dall'utente costituito X e Y coordinate implementate come routine delle proprietà.  
  
 Quando si definisce un tipo definito dall'utente sono richiesti gli spazi dei nomi seguenti:  
  
```vb  
Imports System  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
```  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
```  
  
 Il **SQLServer** spazio dei nomi contiene gli oggetti richiesti per vari attributi del tipo definito dall'utente e il **System.Data.SqlTypes** spazio dei nomi contiene le classi che rappresentano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipi di dati nativi disponibili per l'assembly. Naturalmente, per il corretto funzionamento dell'assembly potrebbero essere necessari altri spazi dei nomi. Il **punto** tipo definito dall'utente utilizza inoltre il **System. Text** dello spazio dei nomi per l'utilizzo di stringhe.  
  
> [!NOTE]  
>  Visual C++ oggetti di database quali tipi definiti dall'utente, compilati con **/clr: pure** non sono supportati per l'esecuzione.  
  
## <a name="specifying-attributes"></a>Specifica degli attributi  
 Gli attributi consentono di determinare la modalità di utilizzo della serializzazione per costruire la rappresentazione di archiviazione dei tipi definiti dall'utente e per trasmettere tali tipi al client in base al valore.  
  
 Il **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** è obbligatorio. Il **Serializable** attributo è facoltativo. È inoltre possibile specificare il **Microsoft.SqlServer.Server.SqlFacetAttribute** per fornire informazioni relative al tipo restituito di un tipo definito dall'utente. Per altre informazioni, vedere [Attributi personalizzati per routine CLR](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).  
  
### <a name="point-udt-attributes"></a>Attributi per il tipo definito dall'utente Point  
 Il **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** imposta il formato di archiviazione per il **punto** tipo definito dall'utente **Native**. **IsByteOrdered** è impostata su **true**, che garantisce che i risultati dei confronti siano uguali in SQL Server come se lo stesso confronto fosse stato effettuato in codice gestito. Il tipo definito dall'utente implementa il **System.Data.SqlTypes.INullable** interfaccia per rendere consapevole il null di tipo definito dall'utente.  
  
 Frammento di codice seguente vengono illustrati gli attributi per il **punto** tipo definito dall'utente.  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True)> _  
  Public Structure Point  
    Implements INullable  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true)]  
public struct Point : INullable  
{  
```  
  
## <a name="implementing-nullability"></a>Implementazione del supporto dei valori Null  
 Oltre a specificare gli attributi per gli assembly in modo corretto, il tipo definito dall'utente deve supportare anche i valori Null. Tipi definiti dall'utente caricati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supportano i valori null, ma affinché il tipo definito dall'utente possa riconoscere un valore null, è necessario che implementi il **System.Data.SqlTypes.INullable** interfaccia.  
  
 È necessario creare una proprietà denominata **IsNull**, che è necessario per determinare se un valore è null dal codice CLR. Quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trova un'istanza Null di un tipo definito dall'utente, tale tipo viene reso persistente utilizzando i normali metodi di gestione dei valori Null. Se non è necessario, nel server non viene eseguita la serializzazione o la deserializzazione del tipo definito dall'utente. Non viene inoltre occupato spazio per l'archiviazione di un tipo definito dall'utente Null. La verifica della presenza di valori Null viene eseguita ogni volta che un tipo definito dall'utente viene importato da CLR. Questo significa che l'utilizzo del costrutto [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL per la verifica dei tipi definiti dall'utente Null dovrebbe funzionare sempre. Il **IsNull** proprietà viene inoltre utilizzata dal server per verificare se un'istanza è null. Una volta stabilito che il tipo definito dall'utente è Null, il server è in grado di utilizzare la relativa funzionalità di gestione nativa dei valori Null.  
  
 Il **Get ()** metodo **IsNull** non/minuscole speciale in alcun modo. Se un **punto** variabile **@p** è **Null**, quindi **@p.IsNull** , per impostazione predefinita, restituirà "NULL", non "1". Infatti, il **SqlMethod(OnNullCall)** attributo del **Get () IsNull** (metodo) valore predefinito è false. Poiché l'oggetto è **Null**, quando la proprietà è richiesta l'oggetto non viene deserializzato, il metodo non viene chiamato e viene restituito un valore predefinito "Null".  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente la variabile `is_Null` è privata e mantiene lo stato Null per l'istanza del tipo definito dall'utente. Il codice deve gestire un valore appropriato per `is_Null`. Il tipo definito dall'utente deve avere anche una proprietà statica denominata **Null** che restituisce un'istanza con valore null del tipo in questione. In questo modo il tipo definito dall'utente può restituire un valore Null se l'istanza è Null nel database.  
  
```vb  
Private is_Null As Boolean  
  
Public ReadOnly Property IsNull() As Boolean _  
   Implements INullable.IsNull  
    Get  
        Return (is_Null)  
    End Get  
End Property  
  
Public Shared ReadOnly Property Null() As Point  
    Get  
        Dim pt As New Point  
        pt.is_Null = True  
        Return (pt)  
    End Get  
End Property  
```  
  
```csharp  
private bool is_Null;  
  
public bool IsNull  
{  
    get  
    {  
        return (is_Null);  
    }  
}  
  
public static Point Null  
{  
    get  
    {  
        Point pt = new Point();  
        pt.is_Null = true;  
        return pt;  
    }  
}  
```  
  
### <a name="is-null-vs-isnull"></a>IS NULL rispetto a IsNull  
 Si consideri una tabella che contiene lo schema Points (id int, punto di posizione), dove **punto** è CLR UDT, mentre le query seguenti:  
  
```  
--Query 1  
SELECT ID  
FROM Points  
WHERE NOT (location IS NULL) -- Or, WHERE location IS NOT NULL;  
```  
  
```  
--Query 2:  
SELECT ID  
FROM Points  
WHERE location.IsNull = 0;  
```  
  
 Entrambe le query restituiscono gli ID dei punti non appartenenti**Null** percorsi. Nella Query 1 viene utilizzata la normale gestione dei valori Null e non è necessaria la deserializzazione dei tipi definiti dall'utente. Query 2, d'altro canto, è necessario deserializzare ogni non -**Null** e chiamare in CLR per ottenere il valore di **IsNull** proprietà. Chiaramente, utilizzando **IS NULL** vengono garantite prestazioni migliori e pertanto non dovrebbe esistere alcun motivo per leggere il **IsNull** proprietà di un tipo definito dall'utente da [!INCLUDE[tsql](../../includes/tsql-md.md)] codice.  
  
 In tal caso, ciò che è l'uso della **IsNull** proprietà? In primo luogo, è necessario determinare se un valore è **Null** dal codice CLR. In secondo luogo, il server deve disporre di un modo per verificare se è un'istanza **Null**, pertanto questa proprietà viene utilizzata dal server. Una volta stabilito che è **Null**, è possibile usare la gestione null nativa per gestirla.  
  
## <a name="implementing-the-parse-method"></a>Implementazione del metodo Parse  
 Il **analizzare** e **ToString** metodi consentono di eseguire conversioni da e verso le rappresentazioni di stringa del tipo in questione. Il **analizzare** metodo consente una stringa da convertire in un tipo definito dall'utente. Deve essere dichiarata come **statici** (o **Shared** in Visual Basic) e accettare un parametro di tipo **System.Data.SqlTypes.SqlString**.  
  
 Il codice seguente implementa la **analizzare** metodo per il **punto** UDT, che separa le coordinate X e Y. Il **analizzare** metodo presenta un solo argomento di tipo **System.Data.SqlTypes.SqlString**e si presuppone che i valori X e Y vengono specificati come una stringa delimitata da virgole. Impostazione di **Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall** attributo **false** impedisce la **analizzare** metodo venga chiamato da un'istanza null di Punto.  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
    return pt;  
}  
```  
  
## <a name="implementing-the-tostring-method"></a>Implementazione del metodo ToString  
 Il **ToString** metodo converte il **punto** tipo definito dall'utente in un valore stringa. In questo caso, viene restituita la stringa "NULL" per un'istanza Null del **punto** tipo. Il **ToString** metodo inverte il **analizzare** metodo con un **StringBuilder** restituire delimitato da virgole **System. String**composta dai valori delle coordinate X e Y. Poiché **InvokeIfReceiverIsNull** valore predefinito è false, il controllo per un'istanza null del **punto** non è necessaria.  
  
```vb  
Private _x As Int32  
Private _y As Int32  
  
Public Overrides Function ToString() As String  
    If Me.IsNull Then  
        Return "NULL"  
    Else  
        Dim builder As StringBuilder = New StringBuilder  
        builder.Append(_x)  
        builder.Append(",")  
        builder.Append(_y)  
        Return builder.ToString  
    End If  
End Function  
```  
  
```csharp  
private Int32 _x;  
private Int32 _y;  
  
public override string ToString()  
{  
    if (this.IsNull)  
        return "NULL";  
    else  
    {  
        StringBuilder builder = new StringBuilder();  
        builder.Append(_x);  
        builder.Append(",");  
        builder.Append(_y);  
        return builder.ToString();  
    }  
}  
```  
  
## <a name="exposing-udt-properties"></a>Esposizione delle proprietà dei tipi definiti dall'utente  
 Il **punto** UDT espone le coordinate X e Y implementate come proprietà pubbliche di lettura / scrittura di tipo **System.Int32**.  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _x = Value  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _y = Value  
    End Set  
End Property  
```  
  
```csharp  
public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    set   
    {  
        _x = value;  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        _y = value;  
    }  
}  
```  
  
## <a name="validating-udt-values"></a>Convalida dei valori dei tipi definiti dall'utente  
 Quando si utilizzano i dati dei tipi definiti dall'utente, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] converte automaticamente i valori binari in valori dei tipi definiti dall'utente. Ai fini di tale processo di conversione, viene verificato che i valori siano appropriati al formato di serializzazione del tipo e che il valore possa essere deserializzato correttamente. In questo modo si garantisce che possa essere convertito il valore nuovo in formato binario. Nel caso dei tipi definiti dall'utente ordinati per byte, questo processo assicura anche che il valore binario risultante corrisponda al valore binario originale. In questo modo si impedisce che valori non validi vengano resi persistenti nel database. In alcuni casi, questo livello di controllo può risultare inadeguato. Una convalida aggiuntiva può essere necessaria quando è necessario che i valori dei tipi definiti dall'utente si trovino in un dominio o in un intervallo previsto. Un tipo definito dall'utente che implementa, ad esempio, una data potrebbe richiedere che il valore del giorno sia un numero positivo compreso in un determinato intervallo di valori validi.  
  
 Il **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName** proprietà del **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** consente di specificare il nome di un metodo di convalida che il server viene eseguita quando i dati sono assegnati a un tipo definito dall'utente oppure convertiti in un tipo definito dall'utente. **Metodo ValidationMethodName** viene chiamato anche durante l'esecuzione dell'utilità bcp, BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, query distribuite e le operazioni di dati tabulari flusso TDS remote procedure call (RPC). Il valore predefinito per **metodo ValidationMethodName** è null, indicando che non vi è alcun metodo di convalida.  
  
### <a name="example"></a>Esempio  
 Frammento di codice seguente viene illustrata la dichiarazione per il **punto** (classe), che specifica un **metodo ValidationMethodName** dei **ValidatePoint**.  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True, _  
  ValidationMethodName:="ValidatePoint")> _  
  Public Structure Point  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true,   
  ValidationMethodName = "ValidatePoint")]  
public struct Point : INullable  
{  
```  
  
 Se si specifica un metodo di convalida, è necessario che includa una firma simile al frammento di codice seguente:  
  
```vb  
Private Function ValidationFunction() As Boolean  
    If (validation logic here) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidationFunction()  
{  
    if (validation logic here)  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
 Il metodo di convalida può disporre di qualsiasi ambito e deve restituire **true** se il valore è valido, e **false** in caso contrario. Se il metodo restituisce **false** o genera un'eccezione, il valore viene trattato non valido e un errore viene generato.  
  
 Nell'esempio riportato di seguito il codice accetta solo valori pari a zero o superiori per le coordinate X e Y.  
  
```vb  
Private Function ValidatePoint() As Boolean  
    If (_x >= 0) And (_y >= 0) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidatePoint()  
{  
    if ((_x >= 0) && (_y >= 0))  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
### <a name="validation-method-limitations"></a>Limitazioni del metodo di convalida  
 Il server chiama il metodo di convalida durante l'esecuzione delle conversioni e non quando i dati vengono inseriti impostando singole proprietà o utilizzando un'istruzione INSERT [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 È necessario chiamare esplicitamente il metodo di convalida da setter di proprietà e il **analizzare** metodo se si desidera che il metodo di convalida da eseguire in tutte le situazioni. Questa operazione non è obbligatoria e in alcuni casi può essere anche sconsigliata.  
  
### <a name="parse-validation-example"></a>Esempio di convalida del metodo Parse  
 Per garantire che il **ValidatePoint** metodo viene richiamato nel **punto** (classe), è necessario chiamarlo dal **analizzare** (metodo) e dalle routine delle proprietà che impostano la X e Y valori delle coordinate. Frammento di codice seguente viene illustrato come chiamare il **ValidatePoint** metodo di convalida dal **analizzare** (funzione).  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
  
    ' Call ValidatePoint to enforce validation  
    ' for string conversions.  
    If Not pt.ValidatePoint() Then  
        Throw New ArgumentException("Invalid XY coordinate values.")  
    End If  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
  
    // Call ValidatePoint to enforce validation  
    // for string conversions.  
    if (!pt.ValidatePoint())   
        throw new ArgumentException("Invalid XY coordinate values.");  
    return pt;  
}  
```  
  
### <a name="property-validation-example"></a>Esempio di convalida delle proprietà  
 Frammento di codice seguente viene illustrato come chiamare il **ValidatePoint** metodo di convalida dalle routine delle proprietà che imposta le coordinate X e Y.  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _x  
        _x = Value  
        If Not ValidatePoint() Then  
            _x = temp  
            Throw New ArgumentException("Invalid X coordinate value.")  
        End If  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _y  
        _y = Value  
        If Not ValidatePoint() Then  
            _y = temp  
            Throw New ArgumentException("Invalid Y coordinate value.")  
        End If  
    End Set  
End Property  
```  
  
```csharp  
    public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    // Call ValidatePoint to ensure valid range of Point values.  
    set   
    {  
        Int32 temp = _x;  
        _x = value;  
        if (!ValidatePoint())  
        {  
            _x = temp;  
            throw new ArgumentException("Invalid X coordinate value.");  
        }  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        Int32 temp = _y;  
        _y = value;  
        if (!ValidatePoint())  
        {  
            _y = temp;  
            throw new ArgumentException("Invalid Y coordinate value.");  
        }  
    }  
}  
```  
  
## <a name="coding-udt-methods"></a>Codifica dei metodi UDT  
 Quando si codificano i metodi UDT, è consigliabile valutare la possibilità che l'algoritmo utilizzato possa cambiare nel tempo. In questo caso è possibile creare una classe separata per i metodi utilizzati dal tipo definito dall'utente. Se l'algoritmo cambia, è possibile ricompilare la classe con il nuovo codice e caricare l'assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza influire sul tipo definito dall'utente. In molti casi i tipi definiti dall'utente possono essere ricaricati utilizzando l'istruzione ALTER ASSEMBLY [!INCLUDE[tsql](../../includes/tsql-md.md)], anche se tale operazione potrebbe provocare problemi con i dati esistenti. Ad esempio, il **valuta** UDT è inclusa la **AdventureWorks** Usa database di esempio un **ConvertCurrency** funzione per convertire i valori di valuta, che è implementata in una classe separata. È possibile che gli algoritmi di conversione cambino nel tempo in modo imprevedibile o che venga richiesta una nuova funzionalità. Separare il **ConvertCurrency** funzione dal **valuta** implementazione del tipo definito dall'utente offre una maggiore flessibilità durante la pianificazione per le modifiche future.  
  
### <a name="example"></a>Esempio  
 Il **punto** classe contiene tre metodi semplici per il calcolo della distanza: **distanza**, **DistanceFrom** e **DistanceFromXY**. Ognuna restituisce un **doppie** calcola la distanza da **punto** a zero, la distanza da un punto specificato alla **punto**, e la distanza specificato le coordinate X e Y per **punto**. **Distanza** e **DistanceFrom** ogni chiamata **DistanceFromXY**e viene illustrato come utilizzare i diversi argomenti per ogni metodo.  
  
```vb  
' Distance from 0 to Point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function Distance() As Double  
    Return DistanceFromXY(0, 0)  
End Function  
  
' Distance from Point to the specified point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFrom(ByVal pFrom As Point) As Double  
    Return DistanceFromXY(pFrom.X, pFrom.Y)  
End Function  
  
' Distance from Point to the specified x and y values.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFromXY(ByVal ix As Int32, ByVal iy As Int32) _  
    As Double  
    Return Math.Sqrt(Math.Pow(ix - _x, 2.0) + Math.Pow(iy - _y, 2.0))  
End Function  
```  
  
```csharp  
// Distance from 0 to Point.  
[SqlMethod(OnNullCall = false)]  
public Double Distance()  
{  
    return DistanceFromXY(0, 0);  
}  
  
// Distance from Point to the specified point.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFrom(Point pFrom)  
{  
    return DistanceFromXY(pFrom.X, pFrom.Y);  
}  
  
// Distance from Point to the specified x and y values.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFromXY(Int32 iX, Int32 iY)  
{  
    return Math.Sqrt(Math.Pow(iX - _x, 2.0) + Math.Pow(iY - _y, 2.0));  
}  
```  
  
### <a name="using-sqlmethod-attributes"></a>Utilizzo degli attributi SqlMethod  
 Il **Microsoft.SqlServer.Server.SqlMethodAttribute** classe fornisce attributi personalizzati che possono essere utilizzati per contrassegnare le definizioni di metodo allo scopo di specificare il determinismo, sul comportamento di chiamate null e indicare se un metodo è un metodo mutatore. Per queste proprietà si presuppone l'uso dei valori predefiniti e l'attributo personalizzato viene utilizzato solo quando è necessario un valore non predefinito.  
  
> [!NOTE]  
>  Il **SqlMethodAttribute** classe eredita il **SqlFunctionAttribute** classe, pertanto **SqlMethodAttribute** eredita il **FillRowMethodName** e **TableDefinition** i campi dal **SqlFunctionAttribute**. Questo implica, contrariamente al vero, la possibilità di scrivere un metodo con valori di tabella. Il metodo viene compilato e l'assembly viene distribuito, ma un errore sul **IEnumerable** restituire tipo viene generato in fase di esecuzione con il messaggio seguente: "metodi, proprietà o campi '\<nome >' nella classe\<(classe) >' nell'assembly '\<assembly >' ha tipo restituito non valido. "  
  
 Nella tabella seguente vengono descritte alcune pertinente **Microsoft.SqlServer.Server.SqlMethodAttribute** le proprietà che possono essere usate nei metodi di tipo definito dall'utente e i relativi valori predefiniti.  
  
 DataAccess  
 Indica se la funzione comporta l'accesso ai dati dell'utente archiviati nell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Valore predefinito è **DataAccessKind**. **Nessuno**.  
  
 IsDeterministic  
 Indica se la funzione produce gli stessi valori di output quando vengono specificati gli stessi valori di input e lo stesso stato del database. Valore predefinito è **false**.  
  
 IsMutator  
 Indica se il metodo causa una modifica dello stato dell'istanza UDT. Valore predefinito è **false**.  
  
 IsPrecise  
 Indica se la funzione comporta calcoli imprecisi, quali operazioni a virgola mobile. Valore predefinito è **false**.  
  
 OnNullCall  
 Indica se il metodo viene chiamato quando vengono specificati argomenti di input con riferimento Null. Valore predefinito è **true**.  
  
### <a name="example"></a>Esempio  
 Il **Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator** proprietà consente di contrassegnare un metodo che consente una modifica nello stato di un'istanza di un tipo definito dall'utente. [!INCLUDE[tsql](../../includes/tsql-md.md)] non consente all'utente di impostare due proprietà del tipo definito dall'utente nella clausola SET di un'istruzione UPDATE. È tuttavia possibile contrassegnare un metodo come mutatore che modifica i due membri.  
  
> [!NOTE]  
>  Nelle query non è consentito l'uso di metodi di tipo mutatore. Tali metodi possono essere chiamati solo nelle istruzioni di assegnazione o nelle istruzioni di modifica dei dati. Se un metodo contrassegnato come mutatore non restituisce **void** (o non è un **Sub** in Visual Basic), CREATE TYPE ha esito negativo con un errore.  
  
 L'istruzione seguente si presuppone l'esistenza di un **triangoli** tipo definito dall'utente che dispone di un **ruota** metodo. I seguenti [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione update richiama il **ruota** metodo:  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 Il **ruota** è decorato con il **SqlMethod** impostazione dell'attributo **IsMutator** a **true** in modo che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possibile contrassegnare il metodo come metodo mutatore. Il codice imposta inoltre **OnNullCall** alla **false**, che indica al server che il metodo restituisce un riferimento null (**Nothing** in Visual Basic) se l'input i parametri sono riferimenti null.  
  
```vb  
<SqlMethod(IsMutator:=True, OnNullCall:=False)> _  
Public Sub Rotate(ByVal anglex as Double, _  
  ByVal angley as Double, ByVal anglez As Double)   
   RotateX(anglex)  
   RotateY(angley)  
   RotateZ(anglez)  
End Sub  
```  
  
```csharp  
[SqlMethod(IsMutator = true, OnNullCall = false)]  
public void Rotate(double anglex, double angley, double anglez)   
{  
   RotateX(anglex);  
   RotateY(angley);  
   RotateZ(anglez);  
}  
```  
  
## <a name="implementing-a-udt-with-a-user-defined-format"></a>Implementazione di un tipo definito dall'utente con un formato definito dall'utente  
 Quando si implementa un tipo definito dall'utente con un formato definito dall'utente, è necessario implementare **Read** e **scrivere** metodi che implementano l'interfaccia Microsoft.SqlServer.Server.IBinarySerialize per gestire la serializzazione e la deserializzazione dei dati di tipo definito dall'utente. È necessario specificare anche il **MaxByteSize** proprietà del **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**.  
  
### <a name="the-currency-udt"></a>Tipo definito dall'utente Currency  
 Il **valuta** viene incluso negli esempi CLR che possono essere installati con tipo definito dall'utente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a partire [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Il **valuta** tipo definito dall'utente supporta la gestione degli importi di denaro nel sistema monetario di una lingua specifica. È necessario definire due campi: una **stringa** per **CultureInfo**, che specifica che ha emesso la valuta (en-us, ad esempio) e un **decimale** per  **CurrencyValue**, la quantità di denaro.  
  
 Anche se non viene utilizzato dal server per l'esecuzione di confronti, il **valuta** UDT implementa il **IComparable** interfaccia, che espone un singolo metodo,  **System.IComparable.CompareTo**. Tale metodo viene utilizzato sul lato client nelle situazioni in cui è consigliabile confrontare o ordinare i valori relativi alla valuta in modo accurato all'interno delle diverse impostazioni cultura.  
  
 Il codice eseguito in CLR confronta le impostazioni cultura separatamente dal valore della valuta. Per il codice [!INCLUDE[tsql](../../includes/tsql-md.md)], il confronto viene determinato dalle azioni seguenti:  
  
1.  Impostare il **IsByteOrdered** attributo su true per indicare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per utilizzare la rappresentazione binaria persistente su disco per i confronti.  
  
2.  Usare la **scrivere** metodo per il **valuta** tipo definito dall'utente per determinare come viene mantenuto il tipo definito dall'utente su disco e come valori di tipo definito dall'utente vengono confrontati e ordinati per [!INCLUDE[tsql](../../includes/tsql-md.md)] operazioni.  
  
3.  Salvare il **valuta** tipo definito dall'utente utilizzando il formato binario seguente:  
  
    1.  Salvare le impostazioni cultura come stringa codificata UTF-16 per i byte 0-19 con riempimento a destra con caratteri Null.  
  
    2.  Utilizzare i byte 20 e successivi per contenere il valore decimale della valuta.  
  
 Lo scopo del riempimento è assicurare che le impostazioni cultura vengano separate completamente dal valore di valuta, in modo che quando un tipo definito dall'utente viene confrontato con un altro tipo nel codice [!INCLUDE[tsql](../../includes/tsql-md.md)], i byte delle impostazioni cultura vengono confrontati con i byte delle impostazioni cultura e i valori dei byte della valuta vengono confrontati con i valori dei byte della valuta.  
  
 Per il codice completo per il **valuta** definito dall'utente, seguire le istruzioni per l'installazione di CLR esempi in [esempi del motore di Database SQL Server](http://msftengprodsamples.codeplex.com/).  
  
### <a name="currency-attributes"></a>Attributi di Currency  
 Il **valuta** è definito con i seguenti attributi.  
  
```vb  
<Serializable(), Microsoft.SqlServer.Server.SqlUserDefinedType( _  
    Microsoft.SqlServer.Server.Format.UserDefined, _  
    IsByteOrdered:=True, MaxByteSize:=32), _  
    CLSCompliant(False)> _  
Public Structure Currency  
Implements INullable, IComparable, _  
Microsoft.SqlServer.Server.IBinarySerialize  
```  
  
```csharp  
[Serializable]  
[SqlUserDefinedType(Format.UserDefined,   
    IsByteOrdered = true, MaxByteSize = 32)]  
    [CLSCompliant(false)]  
    public struct Currency : INullable, IComparable, IBinarySerialize  
    {  
```  
  
## <a name="creating-read-and-write-methods-with-ibinaryserialize"></a>Creazione di metodi di lettura e scrittura con IBinarySerialize  
 Quando si sceglie **UserDefined** formato di serializzazione, è necessario implementare anche il **IBinarySerialize** l'interfaccia e crearne di proprie **lettura** e **scrivere**  metodi. Le procedure riportate di seguito il **valuta** utilizzo di tipo definito dall'utente la **System.IO.BinaryReader** e **System.IO.BinaryWriter** per leggere e scrivere il tipo definito dall'utente.  
  
```vb  
' IBinarySerialize methods  
' The binary layout is as follow:  
'    Bytes 0 - 19: Culture name, padded to the right with null  
'    characters, UTF-16 encoded  
'    Bytes 20+: Decimal value of money  
' If the culture name is empty, the currency is null.  
Public Sub Write(ByVal w As System.IO.BinaryWriter) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Write  
    If Me.IsNull Then  
        w.Write(nullMarker)  
        w.Write(System.Convert.ToDecimal(0))  
        Return  
    End If  
  
    If cultureName.Length > cultureNameMaxSize Then  
        Throw New ApplicationException(String.Format(CultureInfo.CurrentUICulture, _  
           "{0} is an invalid culture name for currency as it is too long.", cultureNameMaxSize))  
    End If  
  
    Dim paddedName As String = cultureName.PadRight(cultureNameMaxSize, CChar(vbNullChar))  
  
    For i As Integer = 0 To cultureNameMaxSize - 1  
        w.Write(paddedName(i))  
    Next i  
  
    ' Normalize decimal value to two places  
    currencyVal = Decimal.Floor(currencyVal * 100) / 100  
    w.Write(currencyVal)  
End Sub  
  
Public Sub Read(ByVal r As System.IO.BinaryReader) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Read  
    Dim name As Char() = r.ReadChars(cultureNameMaxSize)  
    Dim stringEnd As Integer = Array.IndexOf(name, CChar(vbNullChar))  
  
    If stringEnd = 0 Then  
        cultureName = Nothing  
        Return  
    End If  
  
    cultureName = New String(name, 0, stringEnd)  
    currencyVal = r.ReadDecimal()  
End Sub  
  
```  
  
```csharp  
// IBinarySerialize methods  
// The binary layout is as follow:  
//    Bytes 0 - 19:Culture name, padded to the right   
//    with null characters, UTF-16 encoded  
//    Bytes 20+:Decimal value of money  
// If the culture name is empty, the currency is null.  
public void Write(System.IO.BinaryWriter w)  
{  
    if (this.IsNull)  
    {  
        w.Write(nullMarker);  
        w.Write((decimal)0);  
        return;  
    }  
  
    if (cultureName.Length > cultureNameMaxSize)  
    {  
        throw new ApplicationException(string.Format(  
            CultureInfo.InvariantCulture,   
            "{0} is an invalid culture name for currency as it is too long.",   
            cultureNameMaxSize));  
    }  
  
    String paddedName = cultureName.PadRight(cultureNameMaxSize, '\0');  
    for (int i = 0; i < cultureNameMaxSize; i++)  
    {  
        w.Write(paddedName[i]);  
    }  
  
    // Normalize decimal value to two places  
    currencyValue = Decimal.Floor(currencyValue * 100) / 100;  
    w.Write(currencyValue);  
}  
public void Read(System.IO.BinaryReader r)  
{  
    char[] name = r.ReadChars(cultureNameMaxSize);  
    int stringEnd = Array.IndexOf(name, '\0');  
  
    if (stringEnd == 0)  
    {  
        cultureName = null;  
        return;  
    }  
  
    cultureName = new String(name, 0, stringEnd);  
    currencyValue = r.ReadDecimal();  
}  
```  
  
 Per il codice completo per il **valuta** tipo definito dall'utente, vedere [esempi del motore di Database SQL Server](http://msftengprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un tipo definito dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
