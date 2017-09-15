---
title: Recupero di valori in campi di descrizione | Documenti Microsoft
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
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f86dd2e2cb625da359c677fedd297b510fee8593
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Recupero di valori in campi di descrizione
Un'applicazione può chiamare **SQLGetDescField** per ottenere un singolo campo di un record del descrittore. **SQLGetDescField** fornisce l'accesso all'applicazione per tutti i campi di descrizione definiti in ODBC e anche campi definito dal driver.  
  
 **SQLGetDescRec** può essere chiamato per recuperare le impostazioni di più campi di descrizione che interessano il tipo di dati e archiviazione dei dati di colonna o parametro.
