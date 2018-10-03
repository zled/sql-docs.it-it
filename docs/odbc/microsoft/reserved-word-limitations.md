---
title: Limitazioni di Word riservato | Microsoft Docs
ms.custom: ''
ms.date: 05/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ed42f083-c9e8-4ee4-9d64-d879bf955c78
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 531a100fed389264d9af6a1733636792a3dc7920
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764489"
---
# <a name="reserved-keyword-limitations"></a>Limitazioni della parola chiave riservata

Evitare l'utilizzo delle parole chiave riservate di ODBC come identificatori nel tabelle SQL o gli oggetti correlati. Se un caso dispari in cui è necessario usare una parola chiave riservata come identificatore, è necessario racchiudere l'identificatore tra parentesi *apici* ('). Un altro nome per *apice inverso* viene *virgolette inverse*.

La limitazione della parola chiave riservata si applica anche a qualsiasi forma abbreviata delle parole chiave riservate.

Un elenco delle parole chiave riservate di ODBC è disponibile all'indirizzo:

- [Parole chiave riservate di ODBC](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- Nel *Guida di riferimento per programmatori ODBC*, vedere [appendice c: SQL grammatica](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).

