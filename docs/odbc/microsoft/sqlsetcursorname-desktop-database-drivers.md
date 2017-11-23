---
title: SQLSetCursorName (driver di Database Desktop) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLSetCursorName function [ODBC], Desktop Database Drivers
ms.assetid: 9bd7c87b-d99d-4e23-b2db-868d3b461c94
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb398e51768ea9261e360c3ce7088b4ee30ec128
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (driver di Database Desktop)
Poiché il driver non supporta un aggiornamento posizionato o eliminare il WHERE CURRENT OF *nomecursore* sintassi, **SQLSetCursorName** è supportato, ma non può essere utilizzato per gli aggiornamenti posizionati. E può essere utilizzato solo quando è abilitata la libreria di cursori e l'applicazione usa **SQLExtendedFetch**.
