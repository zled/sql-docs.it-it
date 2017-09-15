---
title: Le DLL di installazione traduttore | Documenti Microsoft
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
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dc2fa42c2535d794dcf93160bf79b71d8c226640
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="translator-setup-dlls"></a>DLL di installazione di funzione di conversione
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. Solo in modo esplicito, è necessario installare ODBC nelle versioni precedenti di Windows.  
  
 Il programma di installazione della funzione di conversione DLL contiene il **ConfigTranslator del** funzione, che restituisce l'opzione predefinita per una funzione di conversione. Se necessario, viene richiesto all'utente di queste informazioni. Per una descrizione completa di questa funzione, vedere [riferimento API per l'installazione DLL](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Il programma di installazione del convertitore. DLL è scritta dallo sviluppatore del convertitore. Può essere parte del convertitore di DLL o una DLL separata.
