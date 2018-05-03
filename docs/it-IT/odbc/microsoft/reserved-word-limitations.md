---
title: Limitazioni di Word riservati | Documenti Microsoft
ms.custom: ''
ms.date: 05/01/2018
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
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ed42f083-c9e8-4ee4-9d64-d879bf955c78
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac61a7aa818ef3593fddc630d5027fbf7e4aa211
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="reserved-keyword-limitations"></a>Parola chiave riservata limitazioni

Evitare l'utilizzo delle parole chiave riservate di ODBC come identificatori nel tabelle SQL o gli oggetti correlati. Se un caso dispari in cui è necessario utilizzare una parola chiave riservata come identificatore, è necessario racchiudere l'identificatore con una coppia di *creare righe ininterrotte* ('). Un altro nome per *apice inverso* viene *virgolette inverse*.

La limitazione della parola chiave riservata si applica anche a qualsiasi forma abbreviata delle parole chiave riservate.

Un elenco delle parole chiave riservate di ODBC è disponibile all'indirizzo:

- [Parole chiave riservate di ODBC](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- Nel *Guida di riferimento per programmatori ODBC*, vedere [grammatica SQL di appendice c:](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).

