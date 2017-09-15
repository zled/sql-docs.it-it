---
title: Mapping dei tipi di cursore oggetti Attributes1 informazioni | Documenti Microsoft
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
- compatibility [ODBC], mapping cursor attributes1 information types
- application upgrades [ODBC], mapping cursor attributes1 information types
- mapping cursor attributes1 information types [ODBC]
- backward compatibility [ODBC], mapping cursor attributes1 information types
- upgrading applications [ODBC], mapping cursor attributes1 information types
ms.assetid: 9f112449-ca86-45ac-a865-e6174d67f91b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1d8f72fb4246f2ccfded98e63b701b57d3229068
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Mapping dei tipi di cursore oggetti Attributes1 informazioni
Quando un'applicazione ODBC 3. *x* applicazione chiama **SQLGetInfo** un 2 di ODBC*x* driver con il tipo di informazioni SQL_XXXX_CURSOR_ATTRIBUTES1 (per dinamici e forward-only, i driver, o i cursori statici), l'impostazione dei bit restituiti da Gestione Driver dipende dal quale ODBC 2. *x* driver restituisce per corrispondente ODBC 2.* x* tipi di informazioni. I bit vengono impostati come illustrato nella tabella seguente.  
  
|Bit in<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Tipo di cursore|ODBC 2. *x* informazioni<br /><br /> tipo|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|Tutto|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Dinamico, i driver, statico|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Dinamico, i driver, statico|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|Tutto|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Dinamico, i driver, statico|SQL_POS_OPERATIONS|
