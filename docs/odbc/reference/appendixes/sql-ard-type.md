---
title: SQL_ARD_TYPE | Documenti Microsoft
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
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], SQL_ARD_TYPE
- SQL_ARD_TYPE [ODBC]
ms.assetid: 8d87ca10-f955-4284-8689-e9f4cc31e7ae
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1c789c560adbb01d4c9c0bd2700dd3d1b0757f04
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqlardtype"></a>SQL_ARD_TYPE
L'identificatore di tipo SQL_ARD_TYPE viene utilizzato per indicare che i dati in un buffer sarà del tipo specificato nel campo SQL_DESC_CONCISE_TYPE del ARD. SQL_ARD_TYPE viene immesso nel *TargetType* argomento di una chiamata a **SQLGetData** anziché un tipo di dati specifico e consente a un'applicazione di modificare i dati di tipo di buffer modificando il descrittore campo. Questo valore è il tipo di dati strettamente il  *\*TargetValuePtr* buffer per il campo di descrizione. (SQL_ARD_TYPE non viene immesso in una chiamata a **SQLBindCol** o **SQLBindParameter** perché il tipo di buffer associato è già associato ai campi SQL_DESC_TYPE e SQL_DESC_CONCISE_TYPE e può essere modificato in qualsiasi momento modificando uno di tali campi.)  
  
 L'identificatore di tipo SQL_ARD_TYPE può essere utilizzato per specificare valori non predefiniti per precisione iniziale e la precisione dei tipi di dati di intervallo in secondi, e digitare i valori di precisione e scala per i dati SQL_C_NUMERIC. Per ulteriori informazioni, vedere [override predefinito iniziali e la precisione in secondi per i tipi di dati di intervallo](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md) e [scala per i tipi di dati numerici e si esegue l'override di precisione predefinito](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md), più avanti in questa appendice.
