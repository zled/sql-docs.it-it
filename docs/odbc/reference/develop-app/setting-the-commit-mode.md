---
title: "L'impostazione della modalità di Commit | Documenti Microsoft"
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
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6d0c38d70b859b1fb986ebaa366a5396159a95da
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setting-the-commit-mode"></a>L'impostazione della modalità di Commit
Le applicazioni di specificare la modalità di transazione con l'attributo di connessione SQL_ATTR_AUTOCOMMIT. Per impostazione predefinita, le transazioni ODBC sono in modalità autocommit (a meno che non **SQLSetConnectAttr** e **SQLSetConnectOption** non sono supportati, che è improbabile che). Il passaggio dalla modalità di commit manuale per la modalità autocommit automaticamente viene eseguito il commit di qualsiasi transazione aperta per la connessione.

