---
title: Utilizzo di ADO con Microsoft Visual Basic | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ADO, Visual Basic
- Visual Basic [ADO]
ms.assetid: 9dfb6784-037d-4f9d-bb7f-b506b4498573
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: abeb037ed89277082fce38c833baadc5a4170e3c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="using-ado-with-microsoft-visual-basic-and-visual-basic-for-applications"></a>Utilizzo di ADO con Microsoft Visual Basic e Visual Basic Applications
Impostazione di un progetto ADO e la scrittura di codice ADO è simile se si utilizza Visual Basic o Visual Basic per le applicazioni. In questo argomento risolve l'utilizzo di ADO con Visual Basic e Visual Basic per le applicazioni e rileva eventuali differenze.

## <a name="referencing-the-ado-library"></a>Riferimento alla libreria ADO
 La libreria ADO deve fare riferimento al progetto.

#### <a name="to-reference-ado-from-microsoft-visual-basic"></a>Fare riferimento ad ADO di Microsoft Visual Basic

1.  In Visual Basic dal **progetto** dal menu **riferimenti...** .

2.  Selezionare **Microsoft ActiveX Data Objects x.x. libreria** dall'elenco. Verificare che almeno vengono selezionate anche le librerie seguenti:

    -   Visual Basic, Applications Edition

    -   Procedure e gli oggetti di runtime di Visual Basic

    -   Procedure e gli oggetti di Visual Basic

    -   automazione OLE

3.  Scegliere **OK**.

 È possibile utilizzare ADO con la stessa facilità con Visual Basic per le applicazioni con Microsoft Access, ad esempio.

#### <a name="to-reference-ado-from-microsoft-access"></a>Fare riferimento a ADO da Microsoft Access

1.  In Microsoft Access, selezionare o creare un modulo dal **moduli** nella scheda il **Database** finestra.

2.  Nel **strumenti** dal menu **riferimenti...** .

3.  Selezionare **Microsoft ActiveX Data Objects x.x. libreria** dall'elenco. Verificare che almeno vengono selezionate anche le librerie seguenti:

    -   Visual Basic, Applications Edition

    -   Libreria oggetti di Microsoft Access 8.0 (o versioni successive)

    -   Libreria oggetti di Microsoft DAO 3.5 (o versioni successive)

4.  Scegliere **OK**.

## <a name="creating-ado-objects-in-visual-basic"></a>Creazione di oggetti ADO in Visual Basic
 Per creare una variabile di automazione e un'istanza di un oggetto per tale variabile, è possibile utilizzare due metodi: **Dim** o **CreateObject**.

### <a name="dim"></a>Dim
 È possibile utilizzare il **New** parola chiave with **Dim** dichiarare e creare istanze di oggetti ADO in un unico passaggio:

```
Dim conn As New ADODB.Connection
```

 In alternativa, il **Dim** creazione istanza dichiarazione e l'oggetto istruzione può essere anche i due passaggi:

```
Dim conn As ADODB.Connection
Set conn = New ADODB.Connection
```

> [!NOTE]
>  Non è necessario utilizzare in modo esplicito il `ADODB` progid con il **Dim** istruzione, presupponendo che si è fatto riferimento alla libreria ADO correttamente nel progetto. Utilizzarlo, tuttavia, assicura che non è in conflitto con altre librerie di denominazione.

> [!NOTE]
>  Se si includono riferimenti a ADO e DAO nello stesso progetto, ad esempio, si deve includere un qualificatore per specificare quale modello di oggetto da utilizzare per creare un'istanza di **Recordset** oggetti, come illustrato nel codice seguente:

```
Dim adoRS As ADODB.Recordset
Dim daoRS As DAO.Recordset
```

### <a name="createobject"></a>CreateObject
 Con il **CreateObject** la creazione di istanze di metodo, la dichiarazione e l'oggetto deve essere di due passaggi distinti:

```
Dim conn1
Set conn1 = CreateObject("ADODB.Connection") As Object
```

 Creare istanze degli oggetti con **CreateObject** sono ad associazione tardiva, il che significa che non sono fortemente tipizzati e il completamento della riga di comando è disattivato. Tuttavia, consentono di ignorare che fa riferimento alla libreria ADO dal progetto e consente di creare un'istanza di versioni specifiche di oggetti. Esempio:

```
Set conn1 = CreateObject("ADODB.Connection.2.0") As Object
```

 È inoltre possibile ottenere questo specifico creando un riferimento alla libreria ADO versione 2.0 di tipo e la creazione dell'oggetto.

 Creazione di istanze di oggetti utilizzando il **CreateObject** metodo è in genere più lenta rispetto all'utilizzo di **Dim** istruzione.

## <a name="handling-events"></a>Gestione degli eventi
 Per gestire gli eventi di ADO in Microsoft Visual Basic, è necessario dichiarare una variabile di a livello di modulo utilizzando la **WithEvents** (parola chiave). La variabile può essere dichiarata solo come parte di un modulo di classe e deve essere dichiarata a livello di modulo. Per una descrizione più dettagliata della gestione degli eventi di ADO, vedere [gestione di eventi ADO](../../../ado/guide/data/handling-ado-events.md).

## <a name="visual-basic-examples"></a>Esempi di Visual Basic
 Molti esempi di Visual Basic sono inclusi nella documentazione di ADO. Per ulteriori informazioni, vedere [esempi di codice ADO in Microsoft Visual Basic](../../../ado/reference/ado-api/ado-code-examples-in-visual-basic.md).

## <a name="see-also"></a>Vedere anche
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md) [utilizzo di ADO con Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) [utilizzo di ADO con linguaggi di Scripting](../../../ado/guide/appendixes/using-ado-with-scripting-languages.md)
