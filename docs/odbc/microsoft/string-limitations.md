---
title: Stringa limitazioni | Documenti Microsoft
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
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e6f9d8add08f80b59adaa42f02bc1da006356081
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="string-limitations"></a>Limitazioni di stringa
La lunghezza massima di una stringa di istruzione SQL è 65.000 caratteri.  
  
 Quando viene utilizzato il driver Microsoft Access, SQL-92 solo le costanti stringa (tra virgolette singole, virgolette doppie non) sono supportate.  
  
 Il carattere barra verticale (&#124;) non può essere utilizzato in una stringa, se il carattere è racchiuso tra virgolette indietro o non.  
  
 Per garantire la massima interoperabilità, le applicazioni devono passare stringhe nei parametri, anziché il passaggio tra virgolette stringhe.
