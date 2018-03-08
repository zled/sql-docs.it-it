---
title: Funzioni di ora e data (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
- ODBC date functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], time and date functions
- FoxPro ODBC driver [ODBC], time and date functions
- time and date functions [ODBC]
- ODBC time and date functions [ODBC]
- date functions [ODBC]
ms.assetid: c1fb63b7-af50-45d6-8dec-ae6ea7119527
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 95545399054e35ee9377f2be5ad2569205c64e8b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Funzioni di ora e data (Driver ODBC di Visual FoxPro)
Nella tabella seguente sono elencate le funzioni di data e ora ODBC supportate dal Driver ODBC di Visual FoxPro; Quando la grammatica di Visual FoxPro per la stessa funzione differisce dalla sintassi ODBC, viene elencata l'equivalente di Visual FoxPro.  
  
|Grammatica ODBC|Grammatica di Visual FoxPro|  
|------------------|---------------------------|  
|CURDATE*)*|DATA*)*|  
|CURTIME*)*|TEMPO*)*|  
|DAYNAME*(date_exp)*|CDOW*(date_exp)*|  
|DAYOFMONTH (*date_exp)*|GIORNO*)*|  
|ORA*(time_exp)*||  
|MINUTO*(time_exp)*||  
|MESE*(time_exp)*||  
|MONTHNAME*(date_exp)*|CMONTH*(date_exp)*|  
|ORA*)*|DATETIME*)*|  
|SECONDO*(time_exp)*|SEC*(time_exp)*|  
|SETTIMANA*(date_exp)*||  
|ANNO*(date_exp)*||  
  
 Le funzioni di data e ora seguenti non sono supportate:  
  
 DAYOFYEAR *(date_exp)*  
  
 TRIMESTRE *(date_exp)*  
  
 TIMESTAMPADD *(intervallo di testo, integer_exp timestamp_exp)*  
  
 TIMESTAMPDIFF *(intervallo di testo, timestamp_exp1 timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>Sequenze di Escape ODBC  
 Il driver supporta anche la sequenza di escape ODBC per i dati di data e timestamp. La sintassi della clausola escape è la seguente:  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)—  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)—  
```  
  
 In questa sintassi, **d** indica che *valore* è una data di *aaaa-mm-gg* formato e **Servizi terminal** indica che *valore*  è un timestamp di *aaaa-mm-gg hh: mm:*[. *f...* ] formato. La sintassi abbreviata per i dati di data e il timestamp è come segue:  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Ad esempio, ognuna delle istruzioni seguenti Aggiorna la tabella ALLTYPES utilizzando la sintassi abbreviata di data e il timestamp in un comando SQL UPDATE supportato:  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sulle sequenze di escape, vedere [sequenze di Escape ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) nel *riferimento per programmatori ODBC*.
