---
title: Gli errori di ADO | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [ADO]
ms.assetid: 9bb84114-a1df-4122-a1b8-ad98dcd85cc3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 54a44c69afd01647c5dca1cab97993f890d81c21
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="ado-run-time-errors"></a>Errori di Run-Time ADO
Gli errori di ADO sono segnalati come errori di run-time del programma. È possibile utilizzare il meccanismo di intercettazione degli errori del linguaggio di programmazione per intercettare e gestirli. Ad esempio, in Visual Basic, usare il **in caso di errore** istruzione. In Visual C++, dipende dal metodo utilizzato per accedere alle raccolte di ADO. Con #import, utilizzare un **try-catch** blocco. In caso contrario, i programmatori C++ è necessario recuperare in modo esplicito chiamando un oggetto errore **GetErrorInfo**. Routine sub Visual Basic seguente viene illustrato come intercettare un errore ADO:

```
' BeginErrorHandlingVB01
Private Sub Form_Load()
' Turn on error handling
On Error GoTo FormLoadError

'Open the database and the recordset for processing.
'
Dim strCnn As String
strCnn = "Provider=sqloledb;" & _
    "Data Source=a-iresmi2000;" & _
    "Initial Catalog=Northwind;Integrated Security=SSPI"

' cnn is a Public Connection Object because
' it was defined WithEvents
Set cnn = New ADODB.Connection
cnn.Open strCnn

' The next line of code intentionally causes
' an error by trying to open a connection
' that has already been opened.
cnn.Open strCnn

' rst is a Public Recordset because it
' was defined WithEvents
Set rst = New ADODB.Recordset
rst.Open "Customers", cnn

Exit Sub

' Error handler
FormLoadError:
    Dim strErr As String
    Select Case Err
        Case adErrObjectOpen
            strErr = "Error #" & Err.Number & ": " & Err.Description & vbCrLf
            strErr = strErr & "Error reported by: " & Err.Source & vbCrLf
            strErr = strErr & "Help File: " & Err.HelpFile & vbCrLf
            strErr = strErr & "Topic ID: " & Err.HelpContext
            MsgBox strErr
            Debug.Print strErr
            Err.Clear
            Resume Next
        ' If some other error occurs that
        ' has nothing to do with ADO, show
        ' the number and description and exit.
        Case Else
            strErr = "Error #" & Err.Number & ": " & Err.Description & vbCrLf
            MsgBox strErr
            Debug.Print strErr
            Unload Me
    End Select
End Sub
' EndErrorHandlingVB01
```

 Questo **Form_Load** routine evento crea intenzionalmente un errore durante il tentativo di aprire lo stesso **connessione** oggetto due volte. La seconda volta il **aprire** metodo viene chiamato, il gestore degli errori è attivato. In questo caso l'errore è di tipo **adErrObjectOpen**, in modo che il gestore degli errori viene visualizzato il messaggio seguente prima di riprendere l'esecuzione del programma:

```
Error #3705: Operation is not allowed when the object is open.
Error reported by: ADODB.Connection
Help File: E:\WINNT\HELP\ADO260.CHM Topic ID: 1003705
```

 Il messaggio di errore include le singole delle informazioni fornite da Visual Basic **Err** dell'oggetto, ad eccezione del **Err** valore, che non si applica qui. Il numero di errore indica si è verificato un errore. La descrizione è utile nei casi in cui si desidera gestire personalmente l'errore. È possibile semplicemente passare insieme all'utente. Anche se in genere si desidera utilizzare messaggi personalizzati per l'applicazione, non è possibile prevedere dell'errore. la descrizione fornisce alcune indicazione sulla causa dell'errore. Nell'esempio di codice, l'errore è stato segnalato per il **connessione** oggetto. Verrà visualizzato l'oggetto tipo o a livello di codice ID, ovvero non un nome di variabile.

> [!NOTE]
>  Visual Basic **Err** oggetto contiene solo informazioni relative all'errore più recente. ADO **errori** insieme il **connessione** oggetto contiene uno **errore** oggetto per ogni errore generato dall'operazione ADO più recente. Utilizzare il **errori** insieme anziché il **Err** oggetto per la gestione di più errori. Per ulteriori informazioni sul **errori** insieme, vedere [errori del Provider](../../../ado/guide/data/provider-errors.md). Tuttavia, se non è valido non **connessione** oggetto, il **Err** oggetto è l'unica origine per informazioni sugli errori di ADO.

 I tipi di operazioni possono causare errori di ADO? Gli errori più comuni di ADO possono implicare l'apertura di un oggetto, ad esempio un **connessione** o **Recordset**, il tentativo di aggiornare i dati o chiamare un metodo o una proprietà che non è supportato dal provider.

 Errori OLE DB possono anche essere passati all'applicazione come errori di run-time nel **errori** insieme.

 L'argomento seguente fornisce ulteriori informazioni sugli errori di ADO.

-   [Riferimento all'errore ADO](../../../ado/guide/data/ado-error-reference.md)

