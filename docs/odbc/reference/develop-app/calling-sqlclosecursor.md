---
title: La chiamata di SQLCloseCursor | Documenti Microsoft
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
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ad8a1d13091dd9413afb79b17eb701688d7f902
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="calling-sqlclosecursor"></a>La chiamata di SQLCloseCursor
Poiché **SQLCloseCursor** è quasi identico **SQLFreeStmt** con SQL_CLOSE, gestione Driver non esegue il mapping a questa funzione. Funzioni di sostituzione vengono mappate in modo che esistente ODBC 2*x* applicazioni possono spostare agevolmente ODBC 3. *x* utilizzando le nuove funzioni. Un tale spostamento rende più semplice per tali applicazioni iniziare a utilizzare di nuovo ODBC 3. *x* funzionalità all'interno di codice condizionale modulare. **SQLCloseCursor** non rappresenta alcuna nuova funzionalità. Un'applicazione non ottenere qualsiasi vantaggio spostando in **SQLCloseCursor** da **SQLFreeStmt** con SQL_CLOSE.
