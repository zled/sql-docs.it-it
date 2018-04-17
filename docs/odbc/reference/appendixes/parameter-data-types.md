---
title: Tipi di dati di parametro | Documenti Microsoft
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
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7a198f2bf8b13b5bd4d8424c8fdf41f6352b92a0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="parameter-data-types"></a>Tipi di dati di parametro
Anche se ogni parametro specificato con **SQLBindParameter** viene definito utilizzando un tipo di dati SQL, i parametri in un'istruzione SQL non sono intrinseci dati digitare. Di conseguenza, i marcatori di parametro possono essere inclusi in un'istruzione SQL solo se i tipi di dati possono essere dedotto da un altro operando nell'istruzione. Ad esempio, in un'espressione aritmetica, ad esempio? + COLUMN1, il tipo di dati del parametro può essere dedotto dal tipo di dati della colonna denominata rappresentato da COLUMN1. Se non è possibile determinare il tipo di dati, un'applicazione non è possibile utilizzare un marcatore di parametro.  
  
 La tabella seguente descrive come un tipo di dati viene determinato per diversi tipi di parametri, in conformità con SQL-92. Per una specifica più completa di inferenza il tipo di parametro quando si utilizzano altre clausole SQL, vedere la specifica di SQL-92.  
  
|Posizione del parametro|Si presuppone che il tipo di dati|  
|---------------------------|-----------------------|  
|Un operando di un operatore di confronto o aritmetici binario|Come l'altro operando|  
|Il primo operando in un **BETWEEN** clausola|Identico a quello del secondo operando|  
|Il secondo o terzo operando in un **BETWEEN** clausola|Il primo operando uguale|  
|Un'espressione utilizzata con **IN**|Uguale al primo valore o la colonna di risultati della sottoquery|  
|Valore utilizzato con **IN**|Diverso da quello dell'espressione o il primo valore nel caso di un marcatore di parametro nell'espressione|  
|Un valore del modello usato con **, ad esempio**|VARCHAR|  
|Un valore di aggiornamento utilizzato con **aggiornare**|Stessi valori di aggiornamento|
