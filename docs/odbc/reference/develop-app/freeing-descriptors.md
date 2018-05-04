---
title: Liberazione di descrittori | Documenti Microsoft
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
- SQLFreeHandle function [ODBC]
- descriptors [ODBC], allocating and freeing
- freeing descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0977ba814841ab2fa445a1009262e4a2bfd3a5b3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="freeing-descriptors"></a>Descrittori di rilascio
Possono essere allocata in modo esplicito i descrittori di liberate in modo esplicito, chiamando **SQLFreeHandle** con *HandleType* di SQL_HANDLE_DESC o implicito, quando l'handle di connessione viene liberata. Quando viene liberato un descrittore allocato in modo esplicito, tutti gli handle di istruzione a cui il descrittore liberato applicato automaticamente di ripristinare i descrittori allocati in modo implicito per tali.  
  
 Descrittori allocati in modo implicito possono essere liberati chiamando solo **SQLDisconnect**, che elimina tutte le istruzioni o descrittori aprire per la connessione, oppure chiamando **SQLFreeHandle** con un  *HandleType* impostato su SQL_HANDLE_STMT per liberare un handle di istruzione e i descrittori allocati in modo implicito associati all'istruzione. Un descrittore allocato in modo implicito non può essere liberato chiamando **SQLFreeHandle** con un *HandleType* di SQL_HANDLE_DESC.  
  
 Anche quando liberato, rimane valido, un descrittore allocato in modo implicito e **SQLGetDescField** può essere chiamato nei campi.
