---
title: In generale i comandi di forma | Documenti Microsoft
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
- shape commands [ADO]
- data shaping [ADO], shape commands
ms.assetid: 1fac7831-a187-4b15-9b43-aad380c5556c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2b0998c905e286063cdec6fce3c98f8be2b6937
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="shape-commands-in-general"></a>Comandi Shape in generale
Il data shaping definisce le colonne di una forma **Recordset**, le relazioni tra le entità rappresentate dalle colonne e il modo in cui il **Recordset** viene popolata con dati.  
  
 Una forma **Recordset** può contenere i seguenti tipi di colonne.  
  
|Tipo di colonna|Description|  
|-----------------|-----------------|  
|data|I campi da un **Recordset** restituito da un comando di query a un provider di dati, tabella o la forma in precedenza **Recordset**.|  
|capitolo|Un riferimento a un altro **Recordset**, denominato un *capitolo*. Le colonne a capitoli consentono di definire un *padre-figlio* relazione in cui il *padre* è il **Recordset** che contiene la colonna del capitolo e il *figlio* è il **Recordset** rappresentato dal capitolo.|  
|aggregazione|Il valore della colonna deriva dall'esecuzione di un *funzione di aggregazione* in tutte le righe o una colonna di tutte le righe di un elemento figlio **Recordset**. (Vedere le funzioni di aggregazione nell'argomento seguente [funzioni di aggregazione, la funzione di calcolo e la parola chiave NEW](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md).)|  
|Espressione calcolata|Il valore della colonna è derivato per il calcolo di un'espressione di applicazioni per le colonne nella stessa riga di Visual Basic il **Recordset**. L'espressione è l'argomento della funzione di calcolo. (Vedere espressione calcolata nell'argomento seguente [funzioni di aggregazione, la funzione di calcolo e la parola chiave NEW](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md) e [le funzioni di Visual Basic](../../../ado/guide/data/visual-basic-for-applications-functions.md).)|  
|nuovo|Campi vuoti, creati, che possono essere popolati con dati in un secondo momento. La colonna viene definita con la parola chiave NEW. (Parola chiave NEW nel seguente argomento, vedere [funzioni di aggregazione, la funzione di calcolo e la parola chiave NEW](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md).)|  
  
 Un comando shape può contenere una clausola che specifica un comando di query su un provider di dati sottostante che restituirà un **Recordset** oggetto. La sintassi della query dipende dai requisiti del provider di dati sottostante. Si tratterà in genere SQL, anche se ADO non richiedono l'uso di qualsiasi linguaggio di query specifico.  
  
 Forma comandi possono essere emessi da **Recordset** oggetti oppure impostando il [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) proprietà del [comando](../../../ado/reference/ado-api/command-object-ado.md) e quindi chiamando il [Execute ](../../../ado/reference/ado-api/execute-method-ado-command.md) metodo.  
  
 È possibile utilizzare una clausola JOIN SQL per correlare due tabelle. Tuttavia, un modello gerarchico **Recordset** può rappresentare in modo più efficiente le informazioni. Ogni riga di un **Recordset** creato dalle informazioni di ripetizioni JOIN in modo ridondante da una delle tabelle. Gerarchico **Recordset** presenta un solo padre **Recordset** per ogni figlio più **Recordset** oggetti.  
  
 I comandi di forma possono essere annidati. Vale a dire il *comando padre* o *comando figlio* può essere un altro comando shape.  
  
 Il provider shape restituisce sempre un cursore client, anche quando l'utente specifica una posizione del cursore **adUseServer**.  
  
 È possibile accedere il **Recordset** componenti del data shaping **Recordset** a livello di codice o tramite un controllo visual appropriato.  
  
 Microsoft fornisce uno strumento visivo che genera i comandi di forma (vedere il [dati ambiente progettazione](http://go.microsoft.com/fwlink/?LinkId=5689) nella documentazione di Visual Basic 6) e un altro che consente di visualizzare i cursori gerarchici (vedere "utilizzo di Microsoft gerarchica Controllo FlexGrid"nella documentazione di Visual Basic 6).  
  
 Per informazioni sullo spostamento gerarchico **Recordset**, vedere [accesso alle righe in un Recordset gerarchico](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
 Per informazioni precise sui comandi shape sintatticamente corretti, vedere [grammatica formale di forma](../../../ado/guide/data/formal-shape-grammar.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Funzioni di aggregazione, funzione CALC e parola chiave NEW](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md)  
  
-   [Invio di comandi al provider di dati sottostante](../../../ado/guide/data/issuing-commands-to-the-underlying-data-provider.md)
