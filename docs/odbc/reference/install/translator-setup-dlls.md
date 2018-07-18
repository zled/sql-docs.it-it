---
title: Le DLL di installazione traduttore | Documenti Microsoft
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
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65eca03533940a50a169a948021342f71a032153
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915646"
---
# <a name="translator-setup-dlls"></a>DLL di installazione di funzione di conversione
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. Solo nelle versioni precedenti di Windows è necessario installare ODBC in modo esplicito.  
  
 Il programma di installazione della funzione di conversione DLL contiene il **ConfigTranslator del** funzione, che restituisce l'opzione predefinita per una funzione di conversione. Se necessario, viene richiesto all'utente di queste informazioni. Per una descrizione completa di questa funzione, vedere [riferimento API per l'installazione DLL](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Il programma di installazione del convertitore. DLL è scritta dallo sviluppatore del convertitore. Può essere parte del convertitore di DLL o una DLL separata.
