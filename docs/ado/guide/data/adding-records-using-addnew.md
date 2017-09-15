---
title: Aggiunta di record mediante AddNew | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: cab4adff-f22f-4fb1-9217-f8138c795268
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 92bbc404985ebbb49c4e654efd5a7f54198d35ab
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="adding-records-using-addnew-method"></a>Aggiunta di record mediante AddNew (metodo)
Questa è la sintassi di base di **AddNew** metodo:

 *recordset*. AddNew *elenco campi*, *valori*

 Il *elenco campi* e *valori* gli argomenti sono facoltativi. *Elenco campi* è un singolo nome o una matrice di nomi o posizioni ordinali dei campi nel nuovo record.

 Il *valori* argomento è un singolo valore o una matrice di valori per i campi nel nuovo record.

 In genere, quando si prevede di aggiungere un singolo record, è necessario chiamare il **AddNew** metodo senza argomenti. In particolare, si chiamerà **AddNew**; impostare il **valore** di ogni campo nel nuovo record; e quindi chiamare **aggiornamento** o **UpdateBatch**, o entrambi. È possibile assicurarsi che il **Recordset** supporta l'aggiunta di nuovi record utilizzando il **supporta** proprietà con il **adAddNew** costante enumerata.

 Il codice seguente usa questa tecnica per aggiungere un nuovo spedizioniere per l'esempio **Recordset**. SQL Server fornisce il valore del campo IDCorriere automaticamente. Pertanto, il codice non tenta di fornire un valore di campo per i nuovi record.

```
'BeginAddNew1.1
If objRs.Supports(adAddNew) Then
    With objRs
        .AddNew
        .Fields("CompanyName") = "Sample Shipper"
        .Fields("Phone") = "(931) 555-6334"
        .Update
    End With
End If
'EndAddNew1.1
```

## <a name="remarks"></a>Osservazioni
 Poiché il codice utilizza un disconnesso **Recordset** con un cursore sul lato client in modalità batch, è necessario riconnettere il **Recordset** all'origine dati con un nuovo **connessione** oggetto prima di chiamare il **UpdateBatch** metodo per inviare modifiche al database. Ciò avviene con facilità utilizzando la nuova funzione **GetNewConnection**.

