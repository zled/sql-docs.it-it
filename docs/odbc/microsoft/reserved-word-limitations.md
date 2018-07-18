---
title: Limitazioni di Word riservati | Documenti Microsoft
ms.custom: ''
ms.date: 05/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 010546fe5d0d987443fb4deebc4409cb5e867085
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32901359"
---
# <a name="reserved-keyword-limitations"></a>Parola chiave riservata limitazioni

Evitare l'utilizzo delle parole chiave riservate di ODBC come identificatori nel tabelle SQL o gli oggetti correlati. Se un caso dispari in cui è necessario utilizzare una parola chiave riservata come identificatore, è necessario racchiudere l'identificatore con una coppia di *creare righe ininterrotte* ('). Un altro nome per *apice inverso* viene *virgolette inverse*.

La limitazione della parola chiave riservata si applica anche a qualsiasi forma abbreviata delle parole chiave riservate.

Un elenco delle parole chiave riservate di ODBC è disponibile all'indirizzo:

- [Parole chiave riservate di ODBC](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- Nel *Guida di riferimento per programmatori ODBC*, vedere [grammatica SQL di appendice c:](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).

