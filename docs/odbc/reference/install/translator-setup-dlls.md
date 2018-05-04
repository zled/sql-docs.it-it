---
title: Le DLL di installazione traduttore | Documenti Microsoft
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
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2aabec831ba9b623a24f261551684e9bb259e24
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="translator-setup-dlls"></a>DLL di installazione di funzione di conversione
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. Solo nelle versioni precedenti di Windows è necessario installare ODBC in modo esplicito.  
  
 Il programma di installazione della funzione di conversione DLL contiene il **ConfigTranslator del** funzione, che restituisce l'opzione predefinita per una funzione di conversione. Se necessario, viene richiesto all'utente di queste informazioni. Per una descrizione completa di questa funzione, vedere [riferimento API per l'installazione DLL](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Il programma di installazione del convertitore. DLL è scritta dallo sviluppatore del convertitore. Può essere parte del convertitore di DLL o una DLL separata.
