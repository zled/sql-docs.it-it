---
title: Impostazione della modalità di Commit | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: efc999a3644a9146e7195f0bbbb07d130172d30d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47762399"
---
# <a name="setting-the-commit-mode"></a>Impostazione della modalità di commit
Applicazioni di specificare la modalità di transazione con l'attributo di connessione SQL_ATTR_AUTOCOMMIT. Per impostazione predefinita, le transazioni ODBC sono in modalità autocommit (a meno che **SQLSetConnectAttr** e **SQLSetConnectOption** non sono supportate, che è improbabile). Il passaggio dalla modalità di commit manuale alla modalità di autocommit automaticamente esegue il commit di qualsiasi transazione aperta per la connessione.
