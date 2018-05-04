---
title: Origini dati file | Documenti Microsoft
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
- data sources [ODBC], file
- file data sources [ODBC]
ms.assetid: db245c80-981a-4638-bd03-69d04bc67af0
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 25be6ea116b5449de55aeb8a16ed1cf12e1ce418
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="file-data-sources"></a>Origini dati dei file
*Origini dati del file* vengono archiviati in un file e consentire le informazioni di connessione da usare più volte da un singolo utente o condiviso da più utenti. Quando si utilizza un'origine dati file, Driver Manager esegue la connessione all'origine dati utilizzando le informazioni in un file DSN. Questo file può essere gestito come qualsiasi altro file. Un'origine dati file non dispone di un nome dell'origine dati, come non a un'origine dati macchina e non è registrato a un utente o computer.  
  
 Un'origine dati file semplifica il processo di connessione, perché il file DSN contiene la stringa di connessione che in caso contrario sarebbe di compilazione per una chiamata al **SQLDriverConnect** (funzione). Un altro vantaggio del file DSN è che può essere copiato da qualsiasi computer, in modo da origini di dati identici possono essere utilizzate da molte macchine, purché hanno il driver appropriato installato. Un'origine dati file può essere condivisa anche dalle applicazioni. Un'origine dati file condivisibile può essere inserita in una rete e utilizzare contemporaneamente da più applicazioni.  
  
 Un file DSN può anche essere condivisibile. Un file DSN condivisibili risiede in un singolo computer e punta a un'origine dati macchina. Origini dati su file condivisibile esistano principalmente per consentire la conversione semplice di origini dati macchina in origini dati dei file in modo che un'applicazione può essere progettata per funzionare solo con origini dati dei file. Quando Gestione Driver viene inviata le informazioni in un'origine dati file condivisibile, si connette necessarie per l'origine dati macchina che indichi il file DSN.  
  
 Per ulteriori informazioni sulle origini dati di file, vedere [connessione utilizzando le origini dati](../../odbc/reference/develop-app/connecting-using-file-data-sources.md), o [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) descrizione della funzione.
