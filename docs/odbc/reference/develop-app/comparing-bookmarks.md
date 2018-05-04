---
title: Confronto tra i segnalibri | Documenti Microsoft
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
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cb844592d47e46a38f431f0127845583b82498a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="comparing-bookmarks"></a>Confronto tra i segnalibri
I segnalibri sono confrontabile in termini di byte, essi possono essere confrontati per verificarne l'uguaglianza o disuguaglianza. A tale scopo, un'applicazione gestisce ogni segnalibro come una matrice di byte e consente di confrontare due segnalibri una byte per byte. Poiché i segnalibri sono garantiti come distinti solo all'interno di un set di risultati, è consigliabile non confrontare segnalibri ottenuti da diversi set di risultati.
