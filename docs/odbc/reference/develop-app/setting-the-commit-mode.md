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
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3e3abc5cd7648dce484b6347c30d9290b9fc76a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setting-the-commit-mode"></a>L'impostazione della modalità di Commit
Le applicazioni di specificare la modalità di transazione con l'attributo di connessione SQL_ATTR_AUTOCOMMIT. Per impostazione predefinita, le transazioni ODBC sono in modalità autocommit (a meno che non **SQLSetConnectAttr** e **SQLSetConnectOption** non sono supportati, che è improbabile che). Il passaggio dalla modalità di commit manuale per la modalità autocommit automaticamente viene eseguito il commit di qualsiasi transazione aperta per la connessione.
