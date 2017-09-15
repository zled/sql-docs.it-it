---
title: Rilevamento di troncamento di dati abilitato utilizzando ExtendedAnsiSQL | Documenti Microsoft
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
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 87affbd567a817ea119c405b64f96effe2358052
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Rilevamento di troncamento di dati abilitato utilizzando ExtendedAnsiSQL
Quando è attivato il flag ExtendedAnsiSQL e l'applicazione è di inserimento dei dati in un char o una colonna di dati binari e i dati vengono troncati, verranno rilevati errori di troncamento. Quando il flag ExtendedAnsiSQL è disattivato, i dati vengono troncati senza avviso, come se fosse in versioni precedenti dei driver ODBC Desktop Database.
