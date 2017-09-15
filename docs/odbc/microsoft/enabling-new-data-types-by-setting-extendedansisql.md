---
title: L'abilitazione di nuovi tipi di dati tramite l'impostazione ExtendedAnsiSQL | Documenti Microsoft
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
- extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5161224a5d4fe3f0bf2af200a5cff3e1ea4e1008
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>L'abilitazione di nuovi tipi di dati tramite l'impostazione ExtendedAnsiSQL
Due nuovi tipi di dati sono disponibili nei database Jet 4.0 quando viene attivato il flag ExtendedAnsiSQL: SQL_DECIMAL e SQL_NUMERIC. La precisione predefinita e la scala sono 18 e 0 rispettivamente. Verranno eseguito il mapping di dati a cui accede tramite ODBC tipizzata come SQL_DECIMAL o SQL_NUMERIC per Microsoft Jet decimale invece di valuta.  
  
 Quando il flag ExtendedAnsiSQL è disattivato, è possibile creare tabelle con i tipi di dati decimali o numerici e questi tipi non compariranno nella SQLGetTypeInfo(). Tuttavia, se la tabella contiene nuovi tipi di dati, possono essere utilizzati con i tipi di dati corretto.
