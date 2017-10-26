---
title: CREARE una tabella istruzione limitazioni | Documenti Microsoft
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
- CREATE TABLE statement limitations [ODBC]
- ODBC SQL grammar, CREATE TABLE statement limitations
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0f7cec23f3ec8103b2805e0ee3c0f04d20011cb6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="create-table-statement-limitations"></a>CREARE una tabella istruzione limitazioni
Quando viene utilizzato Paradoxdriver, Microsoft Access o Microsoft Excel e la lunghezza di una colonna di testo o binari non è specificata (o è specificata come 0), la lunghezza della colonna verrà impostata su 255.  
  
 Quando viene utilizzato il driver dBASE e la lunghezza di una colonna di testo o binari non è specificata o è specificata come 0, la lunghezza della colonna verrà impostata su 254.  
  
 È supportato un massimo di 255 colonne.  
  
 Quando il driver di Microsoft Excel è utilizzato in un'origine di 97 dati, un foglio di lavoro o di Microsoft Excel provenienti 5.0, 7.0, non è possibile creare con lo stesso nome di un foglio di lavoro che è stato eliminato in precedenza. Quando il driver per Microsoft Excel viene utilizzato per accedere a un foglio di lavoro versione 5.0, 7.0 o 97, un'istruzione DROP TABLE Cancella il foglio di lavoro, ma non elimina il nome del foglio di lavoro.  
  
 Quando viene utilizzato il driver Paradox, una volta definito un indice in una tabella non è possibile aggiungere colonne. Se la prima colonna dell'elenco di argomenti di un'istruzione CREATE TABLE crea un indice, una seconda colonna non può essere inclusa nell'elenco di argomenti.

