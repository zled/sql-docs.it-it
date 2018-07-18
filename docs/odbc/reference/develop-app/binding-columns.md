---
title: Associazione delle colonne | Documenti Microsoft
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
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b78a87884e075e4cbe3dcb914335994aba2e4159
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908546"
---
# <a name="binding-columns"></a>Associazione delle colonne
Dati recuperati dall'origine dati viene restituiti all'applicazione in variabili che l'applicazione è allocato per questo scopo. Prima di questa operazione può essere eseguita, è necessario associare l'applicazione, o *associare*, impostare queste variabili alle colonne del risultato; concettualmente, questo processo è lo stesso come variabili di applicazione di associazione di parametri dell'istruzione. Quando l'applicazione associa una variabile per un set di risultati colonna, descrive tale variabile, indirizzo, tipo di dati e così via, per il driver. Il driver, queste informazioni vengono memorizzate nella struttura mantenuta per l'istruzione e utilizza le informazioni per restituire il valore della colonna quando viene recuperata la riga.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Associazione di colonne di set di risultati](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Utilizzo di SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
