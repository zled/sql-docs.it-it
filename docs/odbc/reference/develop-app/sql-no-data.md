---
title: SQL_NO_DATA | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 749351694a41764b9b5cc8bf3421340d62626aaf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47739889"
---
# <a name="sqlnodata"></a>SQL_NO_DATA
Quando un'applicazione ODBC 3. *x* applicazione chiama **SQLExecDirect**, **SQLExecute**, oppure **SQLParamData** in un'API ODBC 2. *x* driver di eseguire un aggiornamento con ricerca o eliminare l'istruzione che non influiscono su tutte le righe nell'origine dati, il driver deve restituire SQL_SUCCESS, non SQL_NO_DATA. Quando un'applicazione ODBC 2. *x* o ODBC 3. *x* funziona con un'applicazione ODBC 3. *x* driver chiama **SQLExecDirect**, **SQLExecute**, oppure **SQLParamData** con lo stesso risultato, ODBC 3. *x* driver restituisca SQL_NO_DATA.
