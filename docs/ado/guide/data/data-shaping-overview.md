---
title: Data Shaping Panoramica | Documenti Microsoft
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
helpviewer_keywords:
- data shaping [ADO], overview
ms.assetid: 4cb5fd29-4e56-46ac-ae48-a6771c321c0c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c5ebd3d67ffc5c3f3aba0f481182c5812f4523a5
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="data-shaping-overview"></a>Data Shaping Panoramica
*Il data shaping* significa che la creazione di relazioni gerarchiche tra due o più entità logiche in una query. La gerarchia può essere visualizzata in relazioni padre-figlio tra un record di uno [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)e uno o più record (noto anche come un capitolo) di un altro **Recordset**. In una relazione padre-figlio, l'elemento padre **Recordset** contiene l'elemento figlio **Recordset**. Un esempio di tale relazione gerarchica è customers e orders. Per ogni cliente in un database, possono essere presenti zero o più ordini. La relazione gerarchica può essere ricorsivo, vale a dire che i record nipote possono essere annidati in un record figlio. In sostanza, un record gerarchico può essere annidato a qualsiasi profondità. In pratica, ADO limita la ricorsione a un massimo di 512 **Recordset**s.  
  
 In generale, colonne di una forma **Recordset** può contenere i dati da un provider di dati, ad esempio Microsoft® SQL Server, i riferimenti a un altro **Recordset**, valori derivati da un calcolo su una singola riga di un  **Recordset**, o valori derivati da un'operazione su una colonna di un intero **Recordset**. Una colonna può inoltre essere appena creato e vuota.  
  
 Quando si recupera il valore di una colonna che contiene un riferimento a un altro **Recordset**, ADO restituisce automaticamente l'effettivo **Recordset** rappresentato dal riferimento. Il riferimento a un **Recordset** è effettivamente un riferimento a un sottoinsieme dell'elemento figlio, chiamato un *capitolo*. Un singolo elemento padre può fare riferimento a più elementi figlio **Recordset**.  
  
 Il supporto di ADO per il data shaping consente di eseguire query di un'origine dati e restituire un **Recordset** in cui un record (padre) rappresenta un elemento (figlio) **Recordset**. Nello scenario di ordine cliente, è possibile utilizzare dati di data shaping per recuperare le informazioni dei clienti, nonché gli ordini effettuati da ogni cliente in una singola query. I risultanti **Recordset** è noto anche come forma **Recordset**.  
  
 Inoltre, data shaping in ADO consente di creare nuovi **Recordset** oggetti senza un'origine dati sottostante utilizzando il **nuovo** (parola chiave) per descrivere i campi del padre e figlio  **Recordset**. Il nuovo **Recordset** oggetto può essere popolato con i dati e memorizzato in modo permanente. Gli sviluppatori possono inoltre eseguire vari calcoli o aggregazioni (ad esempio, **somma**, **AVG**, e **MAX**) sui campi figlio. Il data shaping inoltre possibile creare un elemento padre **Recordset** da un elemento figlio **Recordset** raggruppando i record figlio e inserendo una riga nell'oggetto padre per ogni gruppo, l'elemento figlio.  
  
 Regolare SQL consente di recuperare dati usando **JOIN** sintassi, ma questo è possibile inefficiente e difficile da gestire perché dati ridondanti padre viene ripetuti in ogni record restituito per una relazione padre-figlio specificata. Il data shaping possibile correlare un record singolo elemento padre del padre **Recordset** a più record figlio nell'elemento figlio **Recordset**, evitando la ridondanza di un **JOIN**. Maggior parte degli utenti di trovare il padre-figlio più **Recordset** modello di programmazione più naturale e semplice da utilizzare rispetto a singolo **Recordset JOIN** modello.
