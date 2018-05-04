---
title: I segnalibri di lunghezza fissa | Documenti Microsoft
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
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c94d79500047fe1f918689426846a3faa98bb2d7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="fixed-length-bookmarks"></a>Segnalibri di lunghezza fissa
Se un'applicazione ODBC 3*x* driver dovrebbero funzionare con un'API ODBC 2. *x* applicazione che utilizza a lunghezza fissa segnalibri, il driver devono supportare le operazioni seguenti:  
  
-   SQL_UB_ON come valore per l'opzione dell'istruzione SQL_USE_BOOKMARKS. (SQL_UB_ON è deprecato in ODBC 3*x*.)  
  
-   L'opzione dell'istruzione SQL_GET_BOOKMARK.
