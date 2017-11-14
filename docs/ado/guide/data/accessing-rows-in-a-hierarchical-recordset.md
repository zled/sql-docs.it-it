---
title: Accesso alle righe in un Recordset gerarchico | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 25f1d2a1-6d5e-4457-aa07-5db5c75dee18
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1107c5c4aafb0a2e661bbc1307f9aea71b278270
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="accessing-rows-in-a-hierarchical-recordset-example"></a>Accesso alle righe in un Recordset gerarchico (ad esempio)
L'esempio seguente mostra i passaggi necessari per accedere alle righe in un modello gerarchico [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md):

1.  **Recordset** oggetti dal **autori** e **titleauthor** tabelle sono correlate dall'ID autore.

2.  Il ciclo esterno viene visualizzato il nome e cognome, stato e identificazione di ogni autore.

3.  L'oggetto aggiunto **Recordset** per ogni riga viene recuperato dal [campi](../../../ado/reference/ado-api/fields-collection-ado.md) insieme e assegnato a *rstTitleAuthor*.

4.  Il ciclo interno visualizza quattro campi di ogni riga nell'oggetto aggiunto **Recordset**.

 Il [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) è impostata su **false** ai fini dell'illustrazione, in modo che è possibile vedere il capitolo modificare in modo esplicito in ogni iterazione del ciclo esterno. Per rendere più efficiente l'esempio di codice, è possibile spostare l'assegnazione nel passaggio 3 prima della prima riga nel passaggio 2, in modo che l'assegnazione viene eseguita una sola volta. Impostare quindi la [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) proprietà **true**, in modo che *rstTitleAuthor* verrà modificato in modo implicito e automaticamente al capitolo corrispondente ogni volta che *rst* passa a una nuova riga.

## <a name="example"></a>Esempio

```
Sub datashape()
   Dim cnn As New ADODB.Connection
   Dim rst As New ADODB.Recordset
   Dim rstTitleAuthor As New ADODB.Recordset

   cnn.Provider = "MSDataShape"
   cnn.Open    "Data Provider=MSDASQL;" & _
               "Data Source=SRV;Integrated Security=SSPI;Database=Pubs"
' STEP 1
   rst.StayInSync = FALSE
   rst.Open    "SHAPE  {select * from authors} "  & _
               "APPEND ({select * from titleauthor} " & _
               "RELATE au_id TO au_id) AS chapTitleAuthor", _
               cnn
' STEP 2
   While Not rst.EOF
      Debug.Print    rst("au_fname"), rst("au_lname"), _
                     rst("state"), rst("au_id")
' STEP 3
      Set rstTitleAuthor = rst("chapTitleAuthor").Value
' STEP 4
      While Not rstTitleAuthor.EOF
         Debug.Print rstTitleAuthor(0), rstTitleAuthor(1), _
                     rstTitleAuthor(2), rstTitleAuthor(3)
         rstTitleAuthor.MoveNext
      Wend
      rst.MoveNext
   Wend
End Sub
```

## <a name="see-also"></a>Vedere anche
 [Data Shaping Panoramica](../../../ado/guide/data/data-shaping-overview.md) [campo oggetto](../../../ado/reference/ado-api/field-object.md) [campi insieme (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md) [grammatica formale forma](../../../ado/guide/data/formal-shape-grammar.md) [Microsoft servizio Data Shaping per OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) [oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [provider obbligatori per il Data Shaping](../../../ado/guide/data/required-providers-for-data-shaping.md) [forma clausola APPEND](../../../ado/guide/data/shape-append-clause.md) [Forma comandi in genere](../../../ado/guide/data/shape-commands-in-general.md) [clausola COMPUTE Shape](../../../ado/guide/data/shape-compute-clause.md) [le funzioni di Visual Basic](../../../ado/guide/data/visual-basic-for-applications-functions.md)

