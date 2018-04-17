---
title: La sintassi del valore letterale di intervallo | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- literals [ODBC], interval
- interval literals [ODBC]
- ODBC literals [ODBC], interval
ms.assetid: 2f2d22c1-51d6-4055-9f5a-53bc31e9fea0
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c7d3d7d1decc5fa2d847ee32c2df3ee4b434aa9f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="interval-literal-syntax"></a>Sintassi del valore letterale di intervallo
La sintassi seguente viene utilizzata per i valori letterali di intervallo in ODBC.  
  
 *valore letterale di intervallo:: = intervallo* [+*&#124;*-] *intervallo-qualificatore della stringa di intervallo*  
  
 *stringa di intervallo* :: = *offerta* { *anno-mese-literal* &#124; *valore letterale di ora giorno* } *offerta*  
  
 *anno-mese-literal* :: = *-valore dell'anno* &#124; [*anni valore* -] *valore mesi*  
  
 *valore letterale di ora giorno* :: = *intervallo di tempo giorno* &#124; *intervallo di tempo*  
  
 *intervallo di tempo giorno* :: = *-valore dei giorni* [*valore delle ore* [:*-valore dei minuti*[:*-valore dei secondi*]]]  
  
 *intervallo di tempo* :: = *valore delle ore* [:*-valore dei minuti* [:*-valore dei secondi* ]]  
  
 &#124;*-valore dei minuti* [:*-valore dei secondi* ]  
  
 &#124;*-valore dei secondi*  
  
 *valore dell'anno* :: = *valore datetime*  
  
 *valore del mese* :: = *valore datetime*  
  
 *valore dei giorni* :: = *valore datetime*  
  
 *valore delle ore* :: = *valore datetime*  
  
 *valore di minuto* :: = *valore datetime*  
  
 *valore di secondi* :: = *secondi intero* [. [ *frazione di secondi*]]  
  
 *valore intero di secondi* :: = *intero senza segno*  
  
 *frazione di secondi* :: = *intero senza segno*  
  
 *valore DateTime* :: = *intero senza segno*  
  
 *intervallo-qualificatore* :: = *inizio campo* TO *campo Fine* &#124; *singolo campo di data/ora*  
  
 *campo di inizio* :: = *campo di data/ora secondo non* [(*intervallo iniziali-campo precisione* )]  
  
 *fine-field* :: = *campo di data/ora secondo non* &#124; secondo [(*intervallo--secondi-precisione frazionaria*)]  
  
 *campo di data/ora singolo* :: = *campo di data/ora secondo non* [(*intervallo iniziali-campo precisione*)] &#124; secondo [(*intervallo iniziali-campo precisione*  [, (*intervallo--secondi-precisione frazionaria*)]  
  
 *campo Data/ora* :: = *campo di data/ora secondo non* &#124; secondo  
  
 *campo di data/ora secondo non* :: = anno &#124; MONTH &#124; giorno &#124; ore &#124; minuto  
  
 *intervallo--secondi-precisione frazionaria* :: = *intero senza segno*  
  
 *intervallo iniziale-campo precisione* :: = *intero senza segno*  
  
 *offerta* :: = '  
  
 *intero senza segno* :: = *cifra...*
