---
title: Origine dati predefinito | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to data source [ODBC], default data source
- functions [ODBC], data source or driver connections
- data sources [ODBC], default
- default data source [ODBC]
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], default data source
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: dd473cc6-f051-4aa0-ab14-3dd1b37fe99e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 995b47b42691935df0c3aa6d0776af15c99c6551
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="default-data-source"></a>Origine dati predefinita
Il driver può selezionare un'origine dati, l'origine dati predefinita, in alcuni casi in cui l'applicazione non specificare in modo esplicito una chiamata:  
  
-   In una chiamata a **SQLConnect** in cui il *ServerName* argomento è una stringa di lunghezza zero, un puntatore null o DEFAULT.  
  
-   In una chiamata a **SQLDriverConnect** in *InConnectionString* una specifica **DSN**= DEFAULT o specifica con la **DSN** (parola chiave) un origine dati che non è contenuto nelle informazioni di sistema.  
  
 È definito dal driver come specificare l'origine dati predefinita. Questo può comportare un'azione amministrativa e può variare a seconda dell'utente.
