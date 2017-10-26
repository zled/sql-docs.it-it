---
title: SQLSetCursorName (driver di Database Desktop) | Documenti Microsoft
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
- SQLSetCursorName function [ODBC], Desktop Database Drivers
ms.assetid: 9bd7c87b-d99d-4e23-b2db-868d3b461c94
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ee0a3a3d5aa5404a062a11410f0ae2adf072e240
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (driver di Database Desktop)
Poiché il driver non supporta un aggiornamento posizionato o eliminare il WHERE CURRENT OF *nomecursore* sintassi, **SQLSetCursorName** è supportato, ma non può essere utilizzato per gli aggiornamenti posizionati. E può essere utilizzato solo quando è abilitata la libreria di cursori e l'applicazione usa **SQLExtendedFetch**.

