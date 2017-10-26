---
title: I driver di Unicode | Documenti Microsoft
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
- Unicode [ODBC], drivers
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: 3b4742d5-74fb-4aff-aa21-d83a0064d73d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 52afd6864229173b699df74410349b0cac482c98
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="unicode-drivers"></a>Driver di Unicode
Se un driver deve essere un driver Unicode o un driver ANSI dipende interamente la natura dell'origine dati. Se l'origine dati supporta dati Unicode, il driver deve essere un driver di Unicode. Se l'origine dati supporta solo i dati ANSI, il driver deve rimanere un driver ANSI.  
  
 È necessario esportare un driver Unicode **SQLConnectW** venga riconosciuta come un driver Unicode da Gestione Driver.  
  
 Un driver Unicode è necessario accettare le funzioni Unicode (con il suffisso *W*) e archiviare i dati Unicode. È possibile utilizzare anche funzioni ANSI, ma non è necessario. (Gestione Driver non supera una chiamata di funzione ANSI con la *A* suffisso per il driver, ma converte in ANSI funzione senza il suffisso e quindi passa il al driver.)  
  
 Un driver Unicode deve essere in grado di restituire set di risultati in un valore Unicode o ANSI, a seconda dell'associazione dell'applicazione. Se un'applicazione associa a SQL_C_CHAR, il driver Unicode deve convertire i dati SQL_WCHAR SQL_CHAR. Gestione driver verrà eseguito il mapping SQL_C_WCHAR a SQL_C_CHAR per i driver ANSI ma non alcun mapping per i driver di Unicode.  
  
> [!NOTE]  
>  Per determinare il tipo di driver, Driver Manager chiamerà **SQLSetConnectAttr** e impostare l'attributo SQL_ATTR_ANSI_APP al momento della connessione. Se l'applicazione usa le API ANSI, SQL_ATTR_ANSI_APP verrà SQL_AA_TRUE e se viene utilizzato Unicode, verrà impostato su un valore di SQL_AA_FALSE. Questo attributo viene utilizzato in modo che il driver può presentare un comportamento diverso in base al tipo di applicazione. L'attributo non può essere impostato direttamente dall'applicazione e non è supportato da **SQLGetConnectAttr**. Se un driver presenta lo stesso comportamento per applicazioni ANSI e Unicode, per questo attributo deve restituire SQL_ERROR. Se il driver restituisce SQL_SUCCESS, gestione Driver verrà separare le connessioni di ANSI e Unicode quando viene utilizzato il pool di connessioni.

