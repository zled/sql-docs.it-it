---
title: Associazione delle colonne | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 02368c6294ab3eae345c756692cde83a1bc6aed6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="binding-columns"></a>Associazione delle colonne
Dati recuperati dall'origine dati viene restituiti all'applicazione in variabili che l'applicazione è allocato per questo scopo. Prima di questa operazione può essere eseguita, è necessario associare l'applicazione, o *associare*, impostare queste variabili alle colonne del risultato; concettualmente, questo processo è lo stesso come variabili di applicazione di associazione di parametri dell'istruzione. Quando l'applicazione associa una variabile per un set di risultati colonna, descrive tale variabile, indirizzo, tipo di dati e così via, per il driver. Il driver, queste informazioni vengono memorizzate nella struttura mantenuta per l'istruzione e utilizza le informazioni per restituire il valore della colonna quando viene recuperata la riga.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Associazione di colonne di set di risultati](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Utilizzo di SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
