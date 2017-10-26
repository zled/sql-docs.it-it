---
title: Confronto tra i segnalibri | Documenti Microsoft
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
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7ebcf375311af498dbb4c777707b7febcddb05a3
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="comparing-bookmarks"></a>Confronto tra i segnalibri
I segnalibri sono confrontabile in termini di byte, essi possono essere confrontati per verificarne l'uguaglianza o disuguaglianza. A tale scopo, un'applicazione gestisce ogni segnalibro come una matrice di byte e consente di confrontare due segnalibri una byte per byte. Poiché i segnalibri sono garantiti come distinti solo all'interno di un set di risultati, è consigliabile non confrontare segnalibri ottenuti da diversi set di risultati.

