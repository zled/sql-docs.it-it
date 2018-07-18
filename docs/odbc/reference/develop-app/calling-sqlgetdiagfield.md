---
title: La chiamata di funzione SQLGetDiagField | Documenti Microsoft
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
- application upgrades [ODBC], SQLGetDiagField
- backward compatibility [ODBC], SqlGetDiagField
- upgrading applications [ODBC], SQLGetDiagField
- SQLGetDiagField function [ODBC], calling
- compatibility [ODBC], SQLGetDiagField
ms.assetid: 3c4fb606-b81c-4f11-9820-f0a54e3bc401
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b89a561623001091bb3e03cce0b47c59d25493c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908186"
---
# <a name="calling-sqlgetdiagfield"></a>La chiamata di funzione SQLGetDiagField
Quando un'applicazione ODBC 3. *x* applicazione chiama **SQLGetDiagField** un 2 di ODBC*x* driver, il driver restituisce SQL_SUCCESS e le informazioni appropriate nella  *\*DiagInfoPtr* se il *DiagIdentifier* argomento è SQL_DIAG_CLASS_ORIGIN, SQL_DIAG_CLASS_SUBCLASS_ORIGIN, SQL_DIAG_CONNECTION_NAME, SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_ NUMERO, SQL_DIAG_RETURNCODE, SQL_DIAG_SERVER_NAME o SQL_DIAG_SQLSTATE. Tutti gli altri campi di diagnostica restituirà SQL_ERROR.
