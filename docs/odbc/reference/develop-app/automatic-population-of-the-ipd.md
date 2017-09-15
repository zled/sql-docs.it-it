---
title: Il popolamento automatico il IPD | Documenti Microsoft
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
- automatically populating ipd [ODBC]
- descriptors [ODBC], automatically populating ipd
- descriptors [ODBC], allocating and freeing
- ipd [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d637ddfebc0563ed2591740498d519f91e34321e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="automatic-population-of-the-ipd"></a>Popolamento automatico il IPD
Alcuni driver sono in grado di impostare i campi del IPD dopo che è stata preparata una query con parametri. I campi di descrizione vengono automaticamente popolati con informazioni sul parametro, inclusi il tipo di dati, precisione, scala e altre caratteristiche. Ciò equivale a supporto **SQLDescribeParam**. Queste informazioni possono rivelarsi particolarmente utile per un'applicazione non dispone di alcun altro modo per individuare, ad esempio quando una query ad hoc viene eseguita con parametri che l'applicazione non conosce.  
  
 Un'applicazione determina se il driver supporta il popolamento automatico chiamando **SQLGetConnectAttr** con un *attributo* di SQL_ATTR_AUTO_IPD. Se viene restituito SQL_TRUE, il driver supporta e l'applicazione può consentire impostando l'attributo di istruzione SQL_ATTR_ENABLE_AUTO_IPD su SQL_TRUE.  
  
 Quando il popolamento automatico è supportato e abilitato, il driver popola i campi del IPD dopo un'istruzione SQL che contengono marcatori di parametro è stata preparata da una chiamata a **SQLPrepare**. Un'applicazione può recuperare queste informazioni chiamando **SQLGetDescField** o **SQLGetDescRec**, o **SQLDescribeParam**. L'applicazione può utilizzare le informazioni da associare al buffer dell'applicazione più appropriato per un parametro o per specificare una conversione di dati per questo file.  
  
 Il popolamento automatico il IPD potrebbe produrre una riduzione delle prestazioni. Un'applicazione può disattivare tale funzionalità per reimpostare l'attributo di istruzione SQL_ATTR_ENABLE_AUTO_IPD SQL_FALSE (il valore predefinito).
