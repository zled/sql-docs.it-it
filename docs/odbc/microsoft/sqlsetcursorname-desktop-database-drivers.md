---
title: SQLSetCursorName (driver di Database Desktop) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetCursorName function [ODBC], Desktop Database Drivers
ms.assetid: 9bd7c87b-d99d-4e23-b2db-868d3b461c94
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e433e6aee341085965f361992fc8ea9ac8744353
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786259"
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (driver di database desktop)
Poiché il driver non supporta un aggiornamento posizionato o per eliminare il WHERE CURRENT OF *nomecursore* sintassi **SQLSetCursorName** è supportato, ma non può essere usato per gli aggiornamenti posizionati. Può essere utilizzato solo quando è abilitata la libreria di cursori e l'applicazione usa **SQLExtendedFetch**.
