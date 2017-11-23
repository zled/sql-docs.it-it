---
title: Origine dati predefinito | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
ms.openlocfilehash: c27bbdf1bf188ba29fc6ddbb98d1c48ab8a4de7e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="default-data-source"></a>Origine dati predefinita
Il driver può selezionare un'origine dati, l'origine dati predefinita, in alcuni casi in cui l'applicazione non specificare in modo esplicito una chiamata:  
  
-   In una chiamata a **SQLConnect** in cui il *ServerName* argomento è una stringa di lunghezza zero, un puntatore null o DEFAULT.  
  
-   In una chiamata a **SQLDriverConnect** in *InConnectionString* una specifica **DSN**= DEFAULT o specifica con la **DSN** (parola chiave) un origine dati che non è contenuto nelle informazioni di sistema.  
  
 È definito dal driver come specificare l'origine dati predefinita. Questo può comportare un'azione amministrativa e può variare a seconda dell'utente.
