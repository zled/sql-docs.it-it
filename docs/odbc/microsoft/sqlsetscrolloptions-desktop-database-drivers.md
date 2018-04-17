---
title: SQLSetScrollOptions (driver di Database Desktop) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 716a29b89598ead97ae5268dcf850dd4c2c1a38d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (driver di Database Desktop)
I cursori forward e statici sono supportati per SQL_CONCUR_READ_ONLY.  
  
 Sono supportati solo i cursori basati su keyset per un *fConcurrency* argomento di SQL_CONCUR_LOCK.  
  
 Un *fConcurrency* argomento di SQL_CONCUR_ROWVER non è supportata.  
  
 I cursori Dynamic e cursori misti non supportati.
