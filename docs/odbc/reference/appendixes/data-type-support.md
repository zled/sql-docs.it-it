---
title: Supporto del tipo di dati | Documenti Microsoft
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
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 820e48a17e397bc9046c8ca431677074e69b8cb2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-type-support"></a>Supporto dei tipi di dati
Driver ODBC devono supportare almeno uno dei SQL_CHAR e SQL_VARCHAR. Supporto per altri tipi di dati è determinato dal livello di conformità dell'origine dati o del driver SQL-92. Un'applicazione deve chiamare **SQLGetTypeInfo** per determinare i tipi di dati supportati dal driver.  
  
 Per ulteriori informazioni sui tipi di dati, vedere [appendice d: i tipi di dati](../../../odbc/reference/appendixes/appendix-d-data-types.md).
