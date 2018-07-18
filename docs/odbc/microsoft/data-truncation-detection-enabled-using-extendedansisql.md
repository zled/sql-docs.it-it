---
title: Rilevamento di troncamento di dati abilitato utilizzando ExtendedAnsiSQL | Documenti Microsoft
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
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08183430384a7a5ced14871c7bd151cb21c40b2b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Rilevamento di troncamento di dati abilitato utilizzando ExtendedAnsiSQL
Quando è attivato il flag ExtendedAnsiSQL e l'applicazione è di inserimento dei dati in un char o una colonna di dati binari e i dati vengono troncati, verranno rilevati errori di troncamento. Quando il flag ExtendedAnsiSQL è disattivato, i dati vengono troncati senza avviso, come se fosse in versioni precedenti dei driver ODBC Desktop Database.
