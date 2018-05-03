---
title: Aggiunta di record mediante AddNew | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: cab4adff-f22f-4fb1-9217-f8138c795268
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 12645f89fe08e36c024924b5580e4386cb471ee7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
