---
title: Confronto tra i segnalibri | Documenti Microsoft
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
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3d26095cf879859e6ea74784fcf87694ba5eb5d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="comparing-bookmarks"></a>Confronto tra i segnalibri
I segnalibri sono confrontabile in termini di byte, essi possono essere confrontati per verificarne l'uguaglianza o disuguaglianza. A tale scopo, un'applicazione gestisce ogni segnalibro come una matrice di byte e consente di confrontare due segnalibri una byte per byte. Poiché i segnalibri sono garantiti come distinti solo all'interno di un set di risultati, è consigliabile non confrontare segnalibri ottenuti da diversi set di risultati.
