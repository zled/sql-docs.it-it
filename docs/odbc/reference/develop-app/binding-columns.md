---
title: Associazione delle colonne | Documenti Microsoft
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
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5903070b8918baa9734e5d188d90861322b57986
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="binding-columns"></a>Associazione delle colonne
Dati recuperati dall'origine dati viene restituiti all'applicazione in variabili che l'applicazione è allocato per questo scopo. Prima di questa operazione può essere eseguita, è necessario associare l'applicazione, o *associare*, impostare queste variabili alle colonne del risultato; concettualmente, questo processo è lo stesso come variabili di applicazione di associazione di parametri dell'istruzione. Quando l'applicazione associa una variabile per un set di risultati colonna, descrive tale variabile, indirizzo, tipo di dati e così via, per il driver. Il driver, queste informazioni vengono memorizzate nella struttura mantenuta per l'istruzione e utilizza le informazioni per restituire il valore della colonna quando viene recuperata la riga.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Colonne del Set di risultati di associazione](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Utilizzando la funzione SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
