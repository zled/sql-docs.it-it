---
title: Unicode | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode [ODBC]
- Unicode [ODBC], about Unicode
ms.assetid: 113e1c9a-8333-4805-86f2-e4b57ab816a5
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7ec40cc841c073fe66f9537687516f044048a0fc
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="unicode"></a>Unicode
Unicode definisce la codifica dei caratteri in molte lingue.  
  
 Per ulteriori informazioni sullo standard Unicode, vedere [l'Unicode Consortium](http://www.unicode.org).  
  
 Definisce un set di caratteri universali. Una tabella codici ANSI di Windows definisce un set di caratteri, in genere contenente caratteri per una lingua. Può risultare più difficile la scrittura di un'applicazione che è necessario utilizzare tabelle codici diverse.  
  
 Unicode non è necessaria una tabella codici. Viene eseguito il mapping di ogni punto di codice in un singolo carattere in un qualsiasi linguaggio.  
  
 Attualmente, solo Unicode che ODBC supporta la codifica è UCS-2, che utilizza un integer a 16 bit (lunghezza fissa) per rappresentare un carattere. Unicode consente alle applicazioni di utilizzare in diverse lingue.  
  
 La gestione Driver ODBC 3.5 (o versione successiva) è abilitata per Unicode. Ciò influisce su due aree principali: chiamate di funzione e tipi di dati string. Gli argomenti di stringa di gestione Driver mappe funzione e i dati stringa come richiesto dall'applicazione e driver, entrambe le quali può essere abilitata per Unicode o ANSI abilitati. Queste due aree vengono discussi in dettaglio nelle sezioni [gli argomenti della funzione Unicode](../../../odbc/reference/develop-app/unicode-function-arguments.md) e [dati Unicode](../../../odbc/reference/develop-app/unicode-data.md).  
  
 La gestione Driver ODBC 3.5 (o versioni successive) supporta l'utilizzo di un driver di Unicode con un'applicazione Unicode e un'applicazione ANSI. Supporta inoltre l'utilizzo di un driver ANSI con un'applicazione ANSI. Gestione Driver fornisce mapping Unicode-to-ANSI limitato per un'applicazione Unicode utilizzano un driver ANSI.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Argomenti della funzione Unicode](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Dati Unicode](../../../odbc/reference/develop-app/unicode-data.md)
