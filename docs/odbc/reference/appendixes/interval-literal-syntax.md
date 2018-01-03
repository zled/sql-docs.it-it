---
title: La sintassi del valore letterale di intervallo | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- literals [ODBC], interval
- interval literals [ODBC]
- ODBC literals [ODBC], interval
ms.assetid: 2f2d22c1-51d6-4055-9f5a-53bc31e9fea0
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 867bcf39a1cfb7807d8156a172e0a0b764a149f7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="interval-literal-syntax"></a>Sintassi del valore letterale di intervallo
La sintassi seguente viene utilizzata per i valori letterali di intervallo in ODBC.  
  
 *valore letterale di intervallo:: = intervallo* [+*&#124;* -] *intervallo-qualificatore della stringa di intervallo*  
  
 *stringa di intervallo* :: = *offerta* { *anno-mese-literal* &#124; *valore letterale di ora giorno* } *offerta*  
  
 *anno-mese-literal* :: = *anni valore* &#124; [*anni valore* -] *-il valore del mese*  
  
 *valore letterale di ora giorno* :: = *intervallo di tempo giorno* &#124; *intervallo di tempo*  
  
 *intervallo di tempo giorno* :: = *giorni valore* [*valore delle ore* [:*-valore dei minuti*[:*-valore dei secondi*]]]  
  
 *intervallo di tempo* :: = *valore delle ore* [:*-valore dei minuti* [:*-valore dei secondi* ]]  
  
 &#124; *-valore dei minuti* [:*-valore dei secondi* ]  
  
 &#124; *-valore dei secondi*  
  
 *valore dell'anno* :: = *valore datetime*  
  
 *valore del mese* :: = *valore datetime*  
  
 *valore di giorni* :: = *valore datetime*  
  
 *valore delle ore* :: = *valore datetime*  
  
 *valore di minuti* :: = *valore datetime*  
  
 *valore di secondi* :: = *secondi intero* [. [ *frazione di secondi*]]  
  
 *valore intero di secondi* :: = *intero senza segno*  
  
 *frazione di secondi* :: = *intero senza segno*  
  
 *valore DateTime* :: = *intero senza segno*  
  
 *qualificatore di intervallo* :: = *inizio campo* a *Fine campo* &#124; *campo datetime singolo*  
  
 *campo di inizio* :: = *campo di data/ora secondo non* [(*intervallo iniziali-campo precisione* )]  
  
 *Fine campo* :: = *campo di data/ora secondo non* &#124; SECONDO [(*intervallo--secondi-precisione frazionaria*)]  
  
 *campo datetime singolo* :: = *campo di data/ora secondo non* [(*intervallo iniziali-campo precisione*)] &#124; SECONDO [(*intervallo iniziali-campo precisione* [, (*intervallo--secondi-precisione frazionaria*)]  
  
 *campo DateTime* :: = *campo di data/ora secondo non* &#124; SECONDO  
  
 *campo di data/ora secondo non* :: = anno &#124; MESE &#124; GIORNO &#124; ORA &#124; MINUTO  
  
 *intervallo--secondi-precisione frazionaria* :: = *intero senza segno*  
  
 *intervallo iniziale-campo precisione* :: = *intero senza segno*  
  
 *offerta* :: = '  
  
 *intero senza segno* :: = *cifre...*
