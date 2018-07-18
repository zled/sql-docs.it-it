---
title: I caratteri di dati e stringhe C | Documenti Microsoft
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
- data buffers [ODBC], length
- data buffers [ODBC], character data
- buffers [ODBC], C strings
- buffers [ODBC], character data
- character data and buffers [ODBC]
- length of data buffers [ODBC]
- data buffers [ODBC], C strings
- buffers [ODBC], length
- C strings and buffers [ODBC]
ms.assetid: 3a141cb4-229d-4027-9349-615cb2995e36
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c23f124aeba138e0ffecc432f28fde4c11c7d1b2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="character-data-and-c-strings"></a>Dati di tipo carattere e le stringhe C
Parametri di input che fanno riferimento a dati di tipo carattere a lunghezza variabile (ad esempio i nomi delle colonne, i parametri dinamici e i valori di attributo di stringa) hanno un parametro di lunghezza associato. Se l'applicazione termina le stringhe con il carattere null, come avviene in C, viene fornito come argomento la lunghezza in byte della stringa (escluso il carattere di terminazione null) o SQL_NTS (Null-Terminated stringa). Un argomento non negativo lunghezza specifica la lunghezza effettiva della stringa associata. L'argomento length può essere 0 per specificare una stringa di lunghezza zero, che è diverso da un valore NULL. Il valore negativo SQL_NTS indica al driver per determinare la lunghezza della stringa individuando il carattere di terminazione null.  
  
 Quando i dati di tipo carattere viene restituiti dal driver per l'applicazione, il driver deve sempre null-chiuderla. In questo modo l'applicazione di scegliere se gestire i dati come stringa o una matrice di caratteri. Se il buffer dell'applicazione non è sufficientemente grande per restituire tutti i dati di tipo carattere, il driver lo tronca alla lunghezza in byte del buffer meno il numero di byte necessari dal carattere di terminazione null, null termina i dati troncati e lo archivia di buffer. Pertanto, le applicazioni devono sempre allocare spazio aggiuntivo per il carattere di terminazione null in buffer utilizzato per recuperare i dati di tipo carattere. Ad esempio, un buffer di byte di 51 è necessario per recuperare i 50 caratteri dei dati.  
  
 È necessario prestare particolare attenzione per l'applicazione e il driver durante l'invio o recupero di dati di tipo carattere long in parti con **SQLPutData** o **SQLGetData**. Se i dati vengono passati come una serie di stringhe con terminazione null, i caratteri di terminazione null su queste stringhe devono essere rimossi prima che i dati possono essere riassemblati.  
  
 Un numero di programmatori in ODBC è confusi caratteri dei dati e stringhe C. Che si è verificato questo è un elemento dell'utilizzo del linguaggio C quando si definiscono le funzioni ODBC. Se un'applicazione o il driver ODBC utilizza una lingua diversa, ricordare che ODBC è indipendente dal linguaggio, questa confusione è meno probabile che si verificano.  
  
 Quando le stringhe C vengono utilizzate per contenere i dati di tipo carattere, il carattere di terminazione null non viene considerato come parte dei dati e non viene conteggiato come parte della relativa lunghezza in byte. Ad esempio, i dati di carattere "ABC" possono essere mantenuti come stringa C "ABC\0" o la matrice di caratteri {'A', 'B', "C"}. La lunghezza in byte dei dati è 3, viene considerato come una stringa o una matrice di caratteri o meno.  
  
 Sebbene le applicazioni e driver comunemente utilizzare stringhe C (matrici con terminazione null di caratteri) per contenere i dati di tipo carattere, non è necessario eseguire questa operazione. In C, dati di tipo carattere possono anche essere considerati come una matrice di caratteri (senza terminazione null) e la lunghezza di byte passati separatamente nel buffer di lunghezza/indicatore.  
  
 Poiché i dati di tipo carattere possono essere contenuti in una non-matrice con terminazione null e la lunghezza di byte passati separatamente, è possibile incorporare caratteri null nei dati di tipo carattere. Tuttavia, il comportamento delle funzioni ODBC, in questo caso è definito ed è specifico del driver se un driver gestisce correttamente. Di conseguenza, applicazioni interoperative sempre devono gestire i dati di tipo carattere che possono contenere caratteri null incorporati come dati binari.
