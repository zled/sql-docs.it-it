---
title: I segnalibri di lunghezza fissa | Documenti Microsoft
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
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 279b6a3c1f8eb2f1eea5bba35ee10f0a6643fb49
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="fixed-length-bookmarks"></a>Segnalibri di lunghezza fissa
Se un'applicazione ODBC 3*x* driver dovrebbero funzionare con un'API ODBC 2.* x* applicazione che utilizza a lunghezza fissa segnalibri, il driver devono supportare le operazioni seguenti:  
  
-   SQL_UB_ON come valore per l'opzione dell'istruzione SQL_USE_BOOKMARKS. (SQL_UB_ON è deprecato in ODBC 3*x*.)  
  
-   L'opzione dell'istruzione SQL_GET_BOOKMARK.
