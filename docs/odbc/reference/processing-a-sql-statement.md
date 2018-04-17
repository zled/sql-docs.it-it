---
title: L'elaborazione di un'istruzione SQL | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], processing
- SQL [ODBC], processing statements
- statement processing [ODBC]
- SQL statements [ODBC]
- ODBC [ODBC], SQL
ms.assetid: 96270c4f-2efd-4dc1-a985-ed7fd5658db2
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6ad96aa66a68d83677b85ca28cf1f6d0a1fefccf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="processing-a-sql-statement"></a>L'elaborazione di un'istruzione SQL
Prima di illustrare le tecniche per l'utilizzo a livello di codice SQL, è necessario illustrare la modalità di elaborazione di un'istruzione SQL. I passaggi sono comuni a tutti e tre le tecniche, anche se ogni tecnica vengano eseguite in momenti diversi. Nella figura seguente vengono illustrati i passaggi coinvolti nell'elaborazione di un'istruzione SQL, che vengono discussi in tutto il resto di questa sezione.  
  
 ![Passaggi per l'elaborazione di un'istruzione SQL](../../odbc/reference/media/pr01.gif "pr01")  
  
 Per elaborare un'istruzione SQL, un DBMS esegue i seguenti cinque passaggi:  
  
1.  Il sistema DBMS analizza innanzitutto l'istruzione SQL. Viene suddivide l'istruzione in singole parole, denominate token, che consente di verificare che l'istruzione è un verbo valido e clausole valide e così via. In questo passaggio è possibile rilevare gli errori di ortografia e gli errori di sintassi.  
  
2.  Il sistema DBMS convalida l'istruzione. Controlla l'istruzione sulla base di catalogo di sistema. Tutte le tabelle denominate nell'istruzione esistano nel database? Tutte le colonne esistenti e i nomi delle colonne non sono ambigui? L'utente dispone dei privilegi necessari per eseguire l'istruzione? In questo passaggio, è possono rilevare alcuni errori di semantiche.  
  
3.  Il sistema DBMS genera un piano di accesso per l'istruzione. Il piano di accesso è una rappresentazione binaria dei passaggi necessari per eseguire l'istruzione. è l'equivalente DBMS di codice eseguibile.  
  
4.  Il sistema DBMS ottimizza il piano di accesso. Vengono illustrati vari modi per eseguire il piano di accesso. Un indice può essere usato per velocizzare la ricerca? Deve DBMS applicare una condizione di ricerca a una tabella e quindi creare un join di tabella B o deve iniziare con il join e utilizzare la condizione di ricerca in un secondo momento? Una ricerca sequenziale di una tabella di evitare o ridotto a un sottoinsieme della tabella? Dopo avere esplorato le alternative, il sistema DBMS sceglie uno di essi.  
  
5.  Il sistema DBMS esegue l'istruzione eseguendo il piano di accesso.  
  
 La procedura utilizzata per elaborare un'istruzione SQL varia quantità richiedono l'accesso al database e la quantità di tempo che accettano. L'analisi di un'istruzione SQL non richiede l'accesso al database e possono essere eseguita molto rapidamente. L'ottimizzazione, d'altra parte, è una CPU molta elaborare e richiede l'accesso al catalogo di sistema. Per una query complessa, riferita, query optimizer può esplorare migliaia di diverse modalità di esecuzione della stessa query. Tuttavia, il costo di esecuzione della query in modo inefficiente in genere è talmente elevato che più recuperato il tempo dedicato all'ottimizzazione della velocità di esecuzione di query maggiore. Questo è ancora più importante se lo stesso piano di accesso ottimizzato può essere utilizzato più volte per eseguire le query ricorrenti.
