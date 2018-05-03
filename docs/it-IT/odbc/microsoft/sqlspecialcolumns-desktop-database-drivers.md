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
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Desktop Database Drivers
ms.assetid: 3de66fdf-053b-4354-979d-e76a5a5e975f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2d2bfda1bb8732e3036c3803628bbe8247f9e76
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (driver di Database Desktop)
Un indice univoco viene restituito (se presente) per il flag SQL_BEST_ROWID in *fColType*. Non verrà restituito alcun set di risultati per il flag SQL_ROWVER.  
  
 Tutti gli ID di riga hanno un ambito di SQL_SCOPE_CURROW.  
  
 Criteri di ricerca non sono supportata per uno di *szTableQualifier* o *szTableName* argomento.
