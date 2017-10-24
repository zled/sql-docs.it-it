---
title: Utilizzo di sintassi in un'espressione di percorso abbreviata | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- abbreviated syntax [XQuery]
ms.assetid: f83c2e41-5722-47c3-b5b8-bf0f8cbe05d3
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cd4ed101bc96fb8c5c417ec1c47063d747af29df
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="path-expressions---using-abbreviated-syntax"></a>Espressioni di percorso - utilizzando una sintassi abbreviata
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Tutti gli esempi di [espressioni di percorso in XQuery](../xquery/path-expressions-xquery.md) utilizzata la sintassi abbreviata per le espressioni di percorso. La sintassi non abbreviata per un passo dell'asse in un'espressione di percorso include il nome dell'asse e il test di nodo, separati da una coppia di due punti e seguiti da zero o più qualificatori di passo.  
  
 Esempio:  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 Nelle espressioni di percorso, XQuery supporta le abbreviazioni seguenti:  
  
-   Il **figlio** asse è l'asse predefinito. Pertanto, il **figlio::** asse può essere omesso da un passaggio di un'espressione. Ad esempio, è possibile scrivere `/child::ProductDescription/child::Summary` nel formato `/ProductDescription/Summary`.  
  
-   Un **attributo** asse può essere abbreviato in @. Ad esempio, è possibile scrivere `/child::ProductDescription[attribute::ProductModelID=10]` nel formato `/ProudctDescription[@ProductModelID=10]`.  
  
-   Oggetto **descendant-or-self::node()/** può essere abbreviato in / /. Ad esempio, è possibile scrivere `/descendant-or-self::node()/child::act:telephoneNumber` nel formato `//act:telephoneNumber`.  
  
     La query precedente recupera tutti i numeri di telefono archiviati nella colonna AdditionalContactInfo della tabella Contact. Lo schema per la colonna AdditionalContactInfo viene definito in modo che un \<telephoneNumber > elemento può essere visualizzato in qualsiasi punto del documento. Per recuperare tutti i numeri di telefono, pertanto, è necessario eseguire la ricerca in ogni nodo del documento. La ricerca inizia alla radice del documento e continua in tutti i nodi discendenti.  
  
     La query seguente recupera tutti i numeri di telefono relativi a un contatto di un cliente specifico:  
  
    ```  
    SELECT AdditionalContactInfo.query('             
                declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";             
                declare namespace crm="http://schemas.adventure-works.com/Contact/Record";             
                declare namespace ci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";             
                /descendant-or-self::node()/child::act:telephoneNumber             
                ') as result             
    FROM Person.Contact             
    WHERE ContactID=1             
    ```  
  
     Se si sostituisce l'espressione di percorso con la sintassi abbreviata `//act:telephoneNumber`, si ottengono gli stessi risultati.  
  
-   Il **self:: node ()** in un passaggio può essere abbreviato in un punto singolo (.). Tuttavia, non è equivalente o interscambiabile con il punto di **self:: node ()**.  
  
     Ad esempio, nella query seguente, l'utilizzo di un punto rappresenta un valore e non un nodo:  
  
    ```  
    ("abc", "cde")[. > "b"]  
    ```  
  
-   Il **padre:: node ()** in un passaggio può essere abbreviato in un doppio punto (.).  
  
  

