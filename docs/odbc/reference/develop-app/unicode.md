---
title: Unicode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC]
- Unicode [ODBC], about Unicode
ms.assetid: 113e1c9a-8333-4805-86f2-e4b57ab816a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9ee58c367e83a61afef45d7df3358488dcb85a0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821069"
---
# <a name="unicode"></a>Unicode
Unicode consente di definire la codifica dei caratteri in molte lingue.  
  
 Per altre informazioni sullo standard Unicode, vedere [The Unicode Consortium](http://www.unicode.org).  
  
 Definisce un set di caratteri universali. Una tabella codici ANSI di Windows definisce un set di caratteri, in genere contenente caratteri per una lingua. Potrebbe essere più difficile da scrivere un'applicazione che è necessaria per utilizzare tabelle codici diverse.  
  
 Unicode non richiede una tabella codici. Viene eseguito il mapping di ogni punto di codice in un singolo carattere in un qualsiasi linguaggio.  
  
 Attualmente, l'unico Unicode che ODBC supporta la codifica è UCS-2, che utilizza un integer a 16 bit (lunghezza fissa) per rappresentare un carattere. Unicode consente alle applicazioni di lavorare in linguaggi diversi.  
  
 La gestione Driver ODBC 3.5 (o versione successiva) è abilitata per Unicode. Ciò influisce su due aree principali: chiamate di funzione e tipi di dati stringa. Gli argomenti di stringa funzione di gestione Driver mappe e dati di tipo stringa come richiesto dall'applicazione e driver, entrambi possono essere abilitata per Unicode o ANSI abilitati. Queste due aree sono illustrate in dettaglio nelle sezioni [gli argomenti della funzione Unicode](../../../odbc/reference/develop-app/unicode-function-arguments.md) e [dati Unicode](../../../odbc/reference/develop-app/unicode-data.md).  
  
 La gestione Driver ODBC 3.5 (o versioni successive) supporta l'utilizzo di un driver di Unicode con un'applicazione Unicode e nelle applicazioni ANSI. Supporta inoltre l'utilizzo di un driver ANSI con applicazioni ANSI. Gestione Driver fornisce mapping Unicode-to-ANSI limitato per un'applicazione Unicode funziona con un driver ANSI.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Argomenti funzione Unicode](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Dati Unicode](../../../odbc/reference/develop-app/unicode-data.md)
