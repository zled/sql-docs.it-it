---
title: Sintassi dei valori letterali intervallo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], interval
- interval literals [ODBC]
- ODBC literals [ODBC], interval
ms.assetid: 2f2d22c1-51d6-4055-9f5a-53bc31e9fea0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d477dbc6b54d7ebd82b7e2ef8611f5f6dd807e83
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694053"
---
# <a name="interval-literal-syntax"></a>Sintassi dei valori letterali intervallo
La sintassi seguente viene utilizzata per i valori letterali intervallo in ODBC.  
  
 *valore letterale di intervallo:: = intervallo* [+*&#124;*-] *intervallo-qualificatore della stringa di intervallo*  
  
 *intervallo-string* :: = *offerta* { *anno-mese-literal* &#124; *giorno-ora-literal* } *offerta*  
  
 *anno-mese-literal* :: = *valore dell'anno* &#124; [*anni-value* -] *mesi-valore*  
  
 *valore letterale di ora Day* :: = *intervallo di tempo giorno* &#124; *intervallo di tempo*  
  
 *intervallo di tempo Day* :: = *-valore dei giorni* [*-valore delle ore* [:*-valore dei minuti*[:*-valore dei secondi*]]]  
  
 *intervallo di tempo* :: = *-valore delle ore* [:*-valore dei minuti* [:*-valore dei secondi* ]]  
  
 &#124;*-valore dei minuti* [:*-valore dei secondi* ]  
  
 &#124;*-valore dei secondi*  
  
 *valore dell'anno* :: = *valore datetime*  
  
 *valore dei mesi* :: = *valore datetime*  
  
 *valore di giorni* :: = *valore datetime*  
  
 *valore delle ore* :: = *valore datetime*  
  
 *valore dei minuti* :: = *valore datetime*  
  
 *valore dei secondi* :: = *intero di secondi* [. [ *frazione di secondi*]]  
  
 *valore intero di secondi* :: = *unsigned integer*  
  
 *frazione di secondi* :: = *unsigned integer*  
  
 *valore DateTime* :: = *unsigned integer*  
  
 *intervallo-qualifier* :: = *campo inizio* TO *fine-field* &#124; *campo datetime singolo*  
  
 *campo di inizio* :: = *campo di data/ora secondo non* [(*precisione-intervallo-leader-campo* )]  
  
 *fine-field* :: = *campo di data/ora secondo non* &#124; secondo [(*intervallo--secondi-precisione frazionaria*)]  
  
 *campo datetime singolo* :: = *campo di data/ora secondo non* [(*intervallo leader-campo precisione*)] &#124; secondo [(*precisione-intervallo-leader-campo*  [, (*intervallo di--secondi-precisione frazionaria*)]  
  
 *campo di data/ora* :: = *campo di data/ora secondo non* &#124; secondo  
  
 *campo di data/ora secondo non* :: = anno &#124; mese &#124; giorno &#124; ora &#124; minuti  
  
 *intervallo di--secondi-precisione frazionaria* :: = *unsigned integer*  
  
 *intervallo iniziale-campo precisione* :: = *unsigned integer*  
  
 *offerta* :: = '  
  
 *intero senza segno* :: = *cifra...*
