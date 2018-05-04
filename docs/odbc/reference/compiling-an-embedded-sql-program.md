---
title: Compila un programma SQL incorporato | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- compiling embedded SQL programs [ODBC]
- embedded SQL [ODBC]
ms.assetid: 9e94146a-5b80-4a01-b586-1e03ff05b9ac
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e4b89a65475b35b50a968b9497c6d90574c6738
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="compiling-an-embedded-sql-program"></a>Compila un programma SQL incorporato
Poiché un programma SQL incorporato contiene una combinazione di istruzioni SQL e host, non può essere inviato direttamente a un compilatore per il linguaggio host. Al contrario, viene compilato tramite un processo in più passaggi. Anche se questo processo è diverso da un prodotto per un prodotto, i passaggi sono quasi gli stessi per tutti i prodotti.  
  
 Questa illustrazione mostra i passaggi necessari per compilare un programma SQL incorporato.  
  
 ![Passaggi per la compilazione di un programma SQL incorporato](../../odbc/reference/media/pr02.gif "pr02")  
  
 Cinque passaggi coinvolti nella compilazione di un programma SQL incorporato:  
  
1.  Il programma SQL incorporato viene inviato il precompilatore SQL, uno strumento di programmazione. Il precompilatore esegue l'analisi del programma, individua le istruzioni SQL incorporate e li elabora. Un precompilatore diversi è necessario per ogni linguaggio di programmazione supportato dal sistema DBMS. Prodotti DBMS offrono in genere precompilers per uno o più lingue, ad esempio C, Pascal, COBOL, Fortran, Ada, PL / I e varie lingue di assembly.  
  
2.  Il precompilatore produce due file di output. Il primo file è il file di origine, senza le istruzioni SQL incorporate. Al loro posto il precompilatore sostituisce chiamate alle routine DBMS proprietarie che forniscano il collegamento in fase di esecuzione tra il programma e il sistema DBMS. In genere, i nomi e le sequenze di chiamata di queste routine sono note solo per il precompilatore e DBMS; non sono un'interfaccia pubblica per il sistema DBMS. Il secondo file è una copia di tutte le istruzioni di SQL incorporate utilizzata nel programma. Questo file è denominato talvolta un modulo di richiesta di database o nome DBRM.  
  
3.  L'output del file di origine dal precompilatore viene inviato al compilatore standard per l'host del linguaggio (ad esempio, un compilatore C o COBOL) di programmazione. Il compilatore elabora il codice sorgente e produce un codice oggetto come output. Si noti che questo passaggio non ha nulla a che vedere con il sistema DBMS o SQL.  
  
4.  Il linker accetta i moduli di oggetto generati dal compilatore, li collega con le diverse routine di libreria e produce un programma eseguibile. Le routine della libreria collegate il programma eseguibile includono le routine DBMS proprietarie descritte nel passaggio 2.  
  
5.  Il modulo di richiesta del database generato dallo strumento di precompilazione viene inviato a un'utilità di associazione speciale. Questa utilità esamina le istruzioni SQL, analizza, convalida e ottimizza le e produce quindi un piano di accesso per ogni istruzione. Il risultato è un piano di accesso combinato per l'intero programma, che rappresenta una versione eseguibile delle istruzioni SQL incorporate. L'utilità di associazione archivia il piano nel database, assegnando in genere il nome dell'applicazione in uso. Se questo passaggio viene eseguita in fase di compilazione o fase di esecuzione varia a seconda del sistema DBMS.  
  
 Si noti che i passaggi necessari per compilare un programma SQL incorporato correlare strettamente con i passaggi descritti in precedenza nella [l'elaborazione di un'istruzione SQL](../../odbc/reference/processing-a-sql-statement.md). In particolare, si noti che il precompilatore separa le istruzioni SQL dal codice del linguaggio host e l'utilità di associazione analizza e convalida le istruzioni SQL e crea i piani di accesso. Nel passaggio 5 in cui ha luogo in fase di compilazione di DBMS, i primi quattro passaggi di elaborazione di un'istruzione SQL eseguite in fase di compilazione, mentre l'ultimo passaggio (esecuzione) viene eseguita in fase di esecuzione. Questo ha lo scopo di rendere l'esecuzione di query in tali DBMS molto veloce.
