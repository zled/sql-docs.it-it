---
title: SQLSpecialColumns (driver di Database Desktop) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- SQLSpecialColumns function [ODBC], Desktop Database Drivers
ms.assetid: 3de66fdf-053b-4354-979d-e76a5a5e975f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d5292e86e32c495f2491826e74105b9d23e39328
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (driver di Database Desktop)
Un indice univoco viene restituito (se presente) per il flag SQL_BEST_ROWID in *fColType*. Non verrà restituito alcun set di risultati per il flag SQL_ROWVER.  
  
 Tutti gli ID di riga hanno un ambito di SQL_SCOPE_CURROW.  
  
 Criteri di ricerca non sono supportata per uno di *szTableQualifier* o *szTableName* argomento.
