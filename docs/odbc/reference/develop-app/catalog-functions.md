---
title: Funzioni di catalogo | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bbacee234dc9fe0e5aff3278f94ddf4626e31829
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="catalog-functions"></a>Funzioni di catalogo
Tutti i database presentano una struttura che descrive la modalità con cui i dati verranno archiviati nel database. Ad esempio, un database semplice di ordine cliente potrebbe avere la struttura illustrata nella figura seguente, in cui le colonne ID vengono utilizzate per collegare le tabelle.  
  
 ![Viene illustrata la struttura di un database semplice](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Questa struttura, insieme ad altre informazioni, ad esempio privilegi, viene archiviata in un set di tabelle di sistema del database denominato *catalogo,* che è noto anche come un *dizionario dei dati*.  
  
 Un'applicazione può individuare la struttura tramite chiamate al *funzioni di catalogo*. Le funzioni di catalogo restituiscono informazioni nel set di risultati e sono in genere implementata tramite **selezionare** istruzioni eseguite su tabelle nel catalogo. Un'applicazione potrebbe ad esempio richiedere un set di risultati contenente informazioni su tutte le tabelle del sistema o tutte le colonne di una particolare tabella.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Utilizzi dei dati del catalogo](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Funzioni di catalogo in ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
