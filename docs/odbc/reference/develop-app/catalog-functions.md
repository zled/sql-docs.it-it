---
title: Funzioni di catalogo | Documenti Microsoft
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
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 497676e6b87b6603d4bc6cb1615bb1b133c7acd4
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-functions"></a>Funzioni di catalogo
Tutti i database presentano una struttura che descrive la modalità con cui i dati verranno archiviati nel database. Ad esempio, un database semplice di ordine cliente potrebbe avere la struttura illustrata nella figura seguente, in cui le colonne ID vengono utilizzate per collegare le tabelle.  
  
 ![Viene illustrata la struttura di un database semplice](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Questa struttura, insieme ad altre informazioni, ad esempio privilegi, viene archiviata in un set di tabelle di sistema del database denominato *catalogo,* che è noto anche come un *dizionario dei dati*.  
  
 Un'applicazione può individuare la struttura tramite chiamate al *funzioni di catalogo*. Le funzioni di catalogo restituiscono informazioni nel set di risultati e sono in genere implementata tramite **selezionare** istruzioni eseguite su tabelle nel catalogo. Un'applicazione potrebbe ad esempio richiedere un set di risultati contenente informazioni su tutte le tabelle del sistema o tutte le colonne di una particolare tabella.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Utilizzi dei dati del catalogo](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Funzioni di catalogo ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
