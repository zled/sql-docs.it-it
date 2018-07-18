---
title: Forma clausola APPEND | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- data shaping [ADO], APPEND clause
- append clause [ADO]
ms.assetid: f90fcf55-6b24-401d-94e1-d65bd24bd342
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78a1b524d54f77fc5bdcc894c4948ca3139cf334
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="shape-append-clause"></a>Clausola APPEND forma
La clausola APPEND del comando forma aggiunge una o più colonne per un **Recordset**. Spesso, queste colonne sono colonne a capitoli, che fanno riferimento a un elemento figlio **Recordset**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
SHAPE [parent-command [[AS] parent-alias]] APPEND column-list  
```  
  
## <a name="description"></a>Description  
 Le parti di questa clausola sono come segue:  
  
 *parent-command*  
 Zero o uno dei seguenti (è possibile omettere il *comando padre* completamente):  
  
-   Un comando del provider racchiuso tra parentesi graffe ("{}") che restituisce un **Recordset** oggetto. Il comando viene immesso al provider di dati sottostante e la relativa sintassi dipende dai requisiti del provider. Ciò corrisponderà in genere il linguaggio SQL, anche se ADO non richieda qualsiasi linguaggio di query specifico.  
  
-   Un altro comando shape incorporati tra parentesi.  
  
-   La parola chiave nella tabella, seguita dal nome di una tabella nel provider di dati.  
  
 *parent-alias*  
 Alias facoltativo che fa riferimento all'elemento padre **Recordset**.  
  
 *column-list*  
 Uno o più delle operazioni seguenti:  
  
-   Una colonna aggregata.  
  
-   Una colonna calcolata.  
  
-   Una nuova colonna creata utilizzando la clausola di nuovo.  
  
-   Una colonna del capitolo. Definizione di una colonna capitolo è racchiuso tra parentesi ((")"). Vedere la sintassi seguente.  
  
```  
SHAPE [parent-command [[AS] parent-alias]]  
   APPEND (child-recordset [ [[AS] child-alias]   
      RELATE parent-column TO child-column | PARAMETER param-number, ... ])  
   [[AS] chapter-alias]   
   [, ... ]  
```  
  
## <a name="remarks"></a>Osservazioni  
 *child-recordset*  
 -   Un comando del provider racchiuso tra parentesi graffe ("{}") che restituisce un **Recordset** oggetto. Il comando viene immesso al provider di dati sottostante e la relativa sintassi dipende dai requisiti del provider. Ciò corrisponderà in genere il linguaggio SQL, anche se ADO non richieda qualsiasi linguaggio di query specifico.  
  
-   Un altro comando shape incorporati tra parentesi.  
  
-   Il nome di un oggetto esistente a forma di **Recordset**.  
  
-   La parola chiave nella tabella, seguita dal nome di una tabella nel provider di dati.  
  
 *child-alias*  
 Un alias che fa riferimento al figlio **Recordset**.  
  
 *parent-column*  
 Una colonna di **Recordset** restituito dal *comando padre.*  
  
 *child-column*  
 Una colonna di **Recordset** restituito dal *comando figlio*.  
  
 *param-number*  
 Vedere [funzionamento dei comandi con parametri](../../../ado/guide/data/operation-of-parameterized-commands.md).  
  
 *chapter-alias*  
 Un alias che fa riferimento alla colonna del capitolo aggiunta all'elemento padre.  
  
> [!NOTE]
>  Il *"colonna padre* a *colonna figlio"* clausola è effettivamente un elenco, in cui ogni relazione definita è separato da virgola  
  
> [!NOTE]
>  La clausola dopo la parola chiave APPEND è effettivamente un elenco, in cui ogni clausola è separato da una virgola e definisce un'altra colonna da aggiungere all'elemento padre.  
  
## <a name="remarks"></a>Osservazioni  
 Quando si creano i comandi provider dall'input dell'utente come parte di un comando SHAPE, forma verrà considerano fornito dall'utente un comando del provider come stringa opaca e passarli fedelmente al provider. Ad esempio, nel comando SHAPE seguente:  
  
```  
SHAPE {select * from t1} APPEND ({select * from t2} RELATE k1 TO k2)  
```  
  
 FORMA eseguirà due comandi: `select * from t1` e (`select * from t2 RELATE k1 TO k2)`. Se l'utente fornisce un comando composto costituita da più provider comandi separati da punti e virgola, forma non è in grado di distinguere la differenza. Quindi, il comando seguente di forma,  
  
```  
SHAPE {select * from t1; drop table t1} APPEND ({select * from t2} RELATE k1 TO k2)  
```  
  
 SHAPE esegue `select * from t1; drop table t1` e (`select * from t2 RELATE k1 TO k2),` non rendersi conto che `drop table t1` è separato e nel comando in questo caso, dannoso provider. Le applicazioni devono convalidare sempre l'input utente per impedire attacchi potenziali pirata informatico.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Funzionamento dei comandi senza parametri](../../../ado/guide/data/operation-of-non-parameterized-commands.md)  
  
-   [Funzionamento dei comandi con parametri](../../../ado/guide/data/operation-of-parameterized-commands.md)  
  
-   [Comandi ibridi](../../../ado/guide/data/hybrid-commands.md)  
  
-   [Clausole COMPUTE intermedie di Shape](../../../ado/guide/data/intervening-shape-compute-clauses.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Data Shaping di esempio](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica formale forma](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)
