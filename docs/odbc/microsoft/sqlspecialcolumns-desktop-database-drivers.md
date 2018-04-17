---
title: SQLSpecialColumns (driver di Database Desktop) | Documenti Microsoft
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
- SQLSpecialColumns function [ODBC], Desktop Database Drivers
ms.assetid: 3de66fdf-053b-4354-979d-e76a5a5e975f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f8305a2c39eb6b1dadd57c925a0e96564b2f03b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (driver di Database Desktop)
Un indice univoco viene restituito (se presente) per il flag SQL_BEST_ROWID in *fColType*. Non verrà restituito alcun set di risultati per il flag SQL_ROWVER.  
  
 Tutti gli ID di riga hanno un ambito di SQL_SCOPE_CURROW.  
  
 Criteri di ricerca non sono supportata per uno di *szTableQualifier* o *szTableName* argomento.
