---
title: Stringa limitazioni | Documenti Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 740a6688d80d104d483c67c6998d20ec204ab41f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="string-limitations"></a>Limitazioni di stringa
La lunghezza massima di una stringa di istruzione SQL è 65.000 caratteri.  
  
 Quando viene utilizzato il driver Microsoft Access, SQL-92 solo le costanti stringa (tra virgolette singole, virgolette doppie non) sono supportate.  
  
 Il carattere barra verticale (&#124;) non può essere utilizzato in una stringa, se il carattere è racchiuso tra virgolette indietro o No.  
  
 Per garantire la massima interoperabilità, le applicazioni devono passare stringhe nei parametri, anziché il passaggio tra virgolette stringhe.
