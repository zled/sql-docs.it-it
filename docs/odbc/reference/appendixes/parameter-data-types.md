---
title: I tipi di dati parametro | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6c2a73aec119b7572cad93dedb2994235329cb2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826030"
---
# <a name="parameter-data-types"></a>Tipi di dati parametro
Anche se ogni parametro specificato con **SQLBindParameter** è definiti utilizzando un tipo di dati SQL, i parametri in un'istruzione SQL non contengono intrinsechi dati digitare. Di conseguenza, i marcatori di parametro possono essere incluso in un'istruzione SQL solo se i tipi di dati possono essere dedotto da un altro operando nell'istruzione. Ad esempio, in un'espressione aritmetica, ad esempio? + COLUMN1, il tipo di dati del parametro può essere dedotto dal tipo di dati della colonna denominata rappresentato da COLUMN1. Un'applicazione non è possibile utilizzare un marcatore di parametro se non è possibile determinare il tipo di dati.  
  
 La tabella seguente descrive come un tipo di dati viene determinato per diversi tipi di parametri, in conformità con SQL-92. Per una specifica più completa di deduzione del tipo di parametro quando si utilizzano altre clausole SQL, vedere la specifica di SQL-92.  
  
|Posizione del parametro|Si presuppone che il tipo di dati|  
|---------------------------|-----------------------|  
|Un operando di un operatore di confronto o aritmetici binario|Uguale all'altro operando|  
|Il primo operando in un **BETWEEN** clausola|Stesso come il secondo operando|  
|Il secondo o terzo operando in un **BETWEEN** clausola|Il primo operando uguale|  
|Un'espressione utilizzata con **IN**|Uguale al primo valore o la colonna di risultati della sottoquery|  
|Un valore usato con **IN**|Diverso da quello dell'espressione o il primo valore se è presente un marcatore di parametro nell'espressione|  
|Un valore del modello usato con **, ad esempio**|VARCHAR|  
|Un valore di aggiornamento usato con **aggiornare**|Corrisponde alla colonna di aggiornamento|
