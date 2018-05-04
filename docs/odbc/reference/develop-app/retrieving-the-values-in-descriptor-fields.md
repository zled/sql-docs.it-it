---
title: Recupero di valori in campi di descrizione | Documenti Microsoft
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
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b8284167a27439c65256ee4559210843ec7dcffe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Recupero di valori in campi di descrizione
Un'applicazione può chiamare **SQLGetDescField** per ottenere un singolo campo di un record del descrittore. **SQLGetDescField** fornisce l'accesso all'applicazione per tutti i campi di descrizione definiti in ODBC e anche i campi definiti dal driver.  
  
 **SQLGetDescRec** può essere chiamato per recuperare le informazioni di più campi di descrizione che interessano il tipo di dati e l'archiviazione dei dati di colonna o parametro.
