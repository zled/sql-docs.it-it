---
title: Matrici di valori di parametro | Documenti Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 9b572c5b-1dfe-40af-bebd-051548ab6d90
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38dc5fb0ed2286b3077e6198bc978808063b5d2f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="arrays-of-parameter-values"></a>Matrici di valori di parametro
È spesso utile per le applicazioni passare matrici di parametri. Ad esempio, utilizzando le matrici di parametri e una con parametri **inserire** istruzione, un'applicazione è possibile inserire un numero di righe in una sola volta. Esistono diversi vantaggi rispetto all'utilizzo di matrici. In primo luogo, il traffico di rete è ridotto, perché i dati per numerose istruzioni vengono inviati in un singolo pacchetto (se l'origine dati supporta le matrici di parametri in modo nativo). In secondo luogo, alcune origini dati possono eseguire istruzioni SQL tramite matrici più velocemente rispetto all'esecuzione lo stesso numero di istruzioni SQL separate. Infine, quando i dati vengono archiviati in una matrice, come accade spesso per i dati della schermata, l'applicazione può associare tutte le righe in una particolare colonna con una singola chiamata a **SQLBindParameter** e aggiornarle tramite l'esecuzione di una singola istruzione.  
  
 Purtroppo, non a molte origini dati supportano le matrici di parametro. Tuttavia, un driver possibile emulare le matrici di parametri tramite l'esecuzione di un'istruzione SQL una volta per ogni set di valori di parametro. Questo può causare un aumento di velocità perché il driver può quindi preparare l'istruzione che prevede di eseguire una volta per ogni set di parametri. Potrebbe inoltre causare semplificare il codice dell'applicazione.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Associazione delle matrici di parametri](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)  
  
-   [Utilizzo delle matrici di parametri](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)
