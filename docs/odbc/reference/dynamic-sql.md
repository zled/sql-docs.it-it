---
title: Istruzioni SQL dinamiche | Documenti Microsoft
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
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], dynamic SQL
- SQL statements [ODBC], embedded SQL
- dynamic SQL [ODBC]
- SQL [ODBC], dynamic SQL
- embedded SQL [ODBC]
ms.assetid: 0bfb9ab7-9c15-4433-93bc-bad8b6c9d287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d0dab9c38b5fe567664455462f0d229a8235ba99
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="dynamic-sql"></a>SQL dinamica
Sebbene SQL statico funziona bene in molte situazioni, è disponibile una classe di applicazioni in cui l'accesso ai dati non è possibile determinare in anticipo. Si supponga, ad esempio, che consente di immettere una query, il foglio di calcolo inviato per il sistema DBMS per recuperare dati da un foglio di calcolo. Il contenuto di questa query ovviamente non può essere noto al programmatore di quando viene scritto il foglio di calcolo.  
  
 Per risolvere questo problema, il foglio di calcolo utilizza una forma di embedded SQL denominato SQL dinamico. A differenza delle istruzioni SQL statiche, che sono hardcoded nel programma, è possono compilate in fase di esecuzione delle istruzioni SQL dinamiche e inserite in una variabile di stringa host. Vengono quindi inviate al DBMS per l'elaborazione. Poiché il sistema DBMS deve generare un piano di accesso in fase di esecuzione per le istruzioni SQL dinamiche, linguaggio SQL dinamico è in genere inferiore a SQL statico. Quando viene compilato un programma che contiene istruzioni SQL dinamiche, le istruzioni SQL dinamiche non vengono rimosse dal programma, come SQL statico. Al contrario, vengono sostituiti da una chiamata di funzione che passa l'istruzione per il sistema DBMS; le istruzioni SQL statiche nello stesso programma vengono considerate normalmente.  
  
 Il modo più semplice per eseguire un'istruzione SQL dinamica è con un'istruzione EXECUTE IMMEDIATE. Questa istruzione passa l'istruzione SQL per il sistema DBMS per la compilazione e l'esecuzione.  
  
 Uno svantaggio dell'istruzione EXECUTE IMMEDIATE è che il sistema DBMS devono essere eseguiti tramite ognuno dei cinque passaggi di elaborazione di un'istruzione SQL ogni volta che viene eseguita l'istruzione. L'overhead necessario per questo processo può essere significativo se molte istruzioni vengono eseguite in modo dinamico ed è dispendiosa se tali istruzioni sono simili. Per risolvere questa situazione, SQL dinamico offre un formato ottimizzato di esecuzione denominata esecuzione preparata, che utilizza la procedura seguente:  
  
1.  Il programma crea un'istruzione SQL in un buffer, come avviene per l'istruzione EXECUTE IMMEDIATE. Invece di variabili host, è possibile sostituire un punto interrogativo (?) per una costante in un punto qualsiasi nel testo dell'istruzione per indicare che un valore per la costante verrà fornito in un secondo momento. Il punto interrogativo viene chiamato come marcatore di parametro.  
  
2.  Il programma passa l'istruzione SQL per il sistema DBMS con un'istruzione PREPARE, le richieste che il sistema DBMS analizzare, convalidare e ottimizza l'istruzione e generare un'esecuzione piano. Il programma utilizza quindi un'istruzione EXECUTE (non un'istruzione EXECUTE IMMEDIATE) per eseguire l'istruzione PREPARE in un secondo momento. Passa i valori dei parametri per l'istruzione tramite una struttura di dati speciale denominata SQLDA o Area dati di SQL.  
  
3.  Il programma è possibile utilizzare l'istruzione EXECUTE più volte, specificando i valori di parametro diversi ogni volta che viene eseguita l'istruzione dinamica.  
  
 Esecuzione preparata è ancora non lo stesso come SQL statico. In SQL statico, i primi quattro passaggi di elaborazione di un'istruzione SQL è avvenire in fase di compilazione. In esecuzione preparata, questi passaggi vengono ancora eseguiti in fase di esecuzione, ma vengono eseguite solo una volta. esecuzione del piano di viene eseguita solo quando viene chiamata EXECUTE. Ciò consente di eliminare alcuni svantaggi prestazioni inerenti l'architettura di SQL dinamico. Nella figura seguente vengono illustrate le differenze tra SQL statico, dinamico SQL con esecuzione immediata e istruzioni SQL dinamiche con l'esecuzione preparata.
