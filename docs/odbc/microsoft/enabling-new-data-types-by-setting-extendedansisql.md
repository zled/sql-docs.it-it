---
title: L'abilitazione di nuovi tipi di dati tramite l'impostazione ExtendedAnsiSQL | Documenti Microsoft
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
- extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c9f7c4c66bebb2404ef8477ed85e0f36edc1407
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>L'abilitazione di nuovi tipi di dati tramite l'impostazione ExtendedAnsiSQL
Due nuovi tipi di dati sono disponibili nei database Jet 4.0 quando viene attivato il flag ExtendedAnsiSQL: SQL_DECIMAL e SQL_NUMERIC. La precisione predefinita e la scala sono 18 e 0 rispettivamente. Verranno eseguito il mapping di dati a cui accede tramite ODBC tipizzata come SQL_DECIMAL o SQL_NUMERIC per Microsoft Jet decimale invece di valuta.  
  
 Quando il flag ExtendedAnsiSQL è disattivato, è possibile creare tabelle con i tipi di dati decimali o numerici e questi tipi non compariranno nella SQLGetTypeInfo(). Tuttavia, se la tabella contiene nuovi tipi di dati, possono essere utilizzati con i tipi di dati corretto.
