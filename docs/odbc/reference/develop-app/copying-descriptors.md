---
title: Copia i descrittori | Documenti Microsoft
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
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5a09d56193641e899ebe64d5bfb455a06af902f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907746"
---
# <a name="copying-descriptors"></a>Descrittori di copiando
Il **SQLCopyDesc** funzione viene chiamata per copiare i campi di un descrittore del descrittore di un altro. I campi possono essere copiati solo a un descrittore di applicazione o un IPD, ma non a un IRD. I campi possono essere copiati da qualsiasi tipo di descrittore. Vengono copiati solo i campi definiti per i descrittori di origine e di destinazione. **SQLCopyDesc** non copia il campo SQL_DESC_ALLOC_TYPE, perché non è possibile modificare il tipo di allocazione del descrittore. Campi copiati sovrascrivere i campi esistenti.  
  
 Un ARD handle di un'istruzione può essere utilizzato come APD su un altro handle di istruzione. In questo modo un'applicazione copiare le righe tra le tabelle senza copiare i dati a livello di applicazione. A tale scopo, viene riutilizzato un descrittore della riga che descrive una riga recuperata di una tabella come un descrittore del parametro per un parametro in un'istruzione INSERT. Il tipo di informazioni SQL_MAX_CONCURRENT_ACTIVITIES deve essere maggiore di 1 per eseguire questa operazione.
