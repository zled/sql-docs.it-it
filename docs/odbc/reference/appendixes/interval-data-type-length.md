---
title: Lunghezza del tipo di dati di intervallo | Documenti Microsoft
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
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e642685b670fa872c1a34d2d10fed815e5a6fa7e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="interval-data-type-length"></a>Lunghezza del tipo di dati intervallo
Le regole seguenti vengono utilizzate per determinare la lunghezza di un tipo di dati di intervallo in caratteri. Lunghezza è espressa in numero di caratteri. Il numero di byte dipende dal set di caratteri. La lunghezza include i seguenti valori aggiunti insieme:  
  
-   Due caratteri per ogni campo nell'intervallo che non è il campo iniziale.  
  
-   Per il campo iniziale, il numero di caratteri che rappresenta la precisione iniziale espressa o implicita. Se la precisione iniziale non è specificata, il valore predefinito è 2.  
  
-   Un carattere per il separatore tra i campi.  
  
-   Uno più la precisione dei secondi espressa o implicita. Se la precisione dei secondi non è specificata, il valore predefinito è 6.  
  
 I valori di lunghezza di colonna specifica per ogni tipo di dati di intervallo sono contenuti in [dimensioni della colonna](../../../odbc/reference/appendixes/column-size.md).

