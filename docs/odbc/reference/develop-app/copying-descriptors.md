---
title: Copia i descrittori | Documenti Microsoft
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
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8cd2ea29713d3bf1e05e76de21397f71dd30c824
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="copying-descriptors"></a>Descrittori di copiando
Il **SQLCopyDesc** funzione viene chiamata per copiare i campi di un descrittore del descrittore di un altro. I campi possono essere copiati solo a un descrittore di applicazione o un IPD, ma non a un IRD. I campi possono essere copiati da qualsiasi tipo di descrittore. Vengono copiati solo i campi definiti per i descrittori di origine e di destinazione. **SQLCopyDesc** non copia il campo SQL_DESC_ALLOC_TYPE, perché il tipo di allocazione di un descrittore non può essere modificato. Campi copiati sovrascrivere i campi esistenti.  
  
 Un ARD handle di un'istruzione può essere utilizzato come APD su un altro handle di istruzione. In questo modo un'applicazione copiare le righe tra le tabelle senza copiare i dati a livello di applicazione. A tale scopo, viene riutilizzato un descrittore della riga che descrive una riga recuperata di una tabella come un descrittore del parametro per un parametro in un'istruzione INSERT. Il tipo di informazioni SQL_MAX_CONCURRENT_ACTIVITIES deve essere maggiore di 1 per eseguire questa operazione.

