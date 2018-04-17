---
title: L'impostazione della modalità di Commit | Documenti Microsoft
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
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 45e975f0cb9ccc78a7cadd4f1a71b046528a9c10
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setting-the-commit-mode"></a>L'impostazione della modalità di Commit
Le applicazioni di specificare la modalità di transazione con l'attributo di connessione SQL_ATTR_AUTOCOMMIT. Per impostazione predefinita, le transazioni ODBC sono in modalità autocommit (a meno che non **SQLSetConnectAttr** e **SQLSetConnectOption** non sono supportati, che è improbabile che). Il passaggio dalla modalità di commit manuale per la modalità autocommit automaticamente viene eseguito il commit di qualsiasi transazione aperta per la connessione.
