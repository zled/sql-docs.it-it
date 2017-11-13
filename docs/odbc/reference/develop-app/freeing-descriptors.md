---
title: Liberazione di descrittori | Documenti Microsoft
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
- SQLFreeHandle function [ODBC]
- descriptors [ODBC], allocating and freeing
- freeing descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d1c70c82196907fc0bd9747a8ece089d4e4ab514
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="freeing-descriptors"></a>Descrittori di rilascio
Possono essere allocata in modo esplicito i descrittori di liberate in modo esplicito, chiamando **SQLFreeHandle** con *HandleType* di SQL_HANDLE_DESC o implicito, quando l'handle di connessione viene liberata. Quando viene liberato un descrittore allocato in modo esplicito, tutti gli handle di istruzione a cui il descrittore liberato applicato automaticamente di ripristinare i descrittori allocati in modo implicito per tali.  
  
 Descrittori allocati in modo implicito possono essere liberati chiamando solo **SQLDisconnect**, che elimina tutte le istruzioni o descrittori aprire per la connessione, oppure chiamando **SQLFreeHandle** con un  *HandleType* impostato su SQL_HANDLE_STMT per liberare un handle di istruzione e i descrittori allocati in modo implicito associati all'istruzione. Un descrittore allocato in modo implicito non può essere liberato chiamando **SQLFreeHandle** con un *HandleType* di SQL_HANDLE_DESC.  
  
 Anche quando liberato, rimane valido, un descrittore allocato in modo implicito e **SQLGetDescField** può essere chiamato nei campi.

