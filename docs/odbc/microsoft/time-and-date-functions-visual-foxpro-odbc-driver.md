---
title: Funzioni di ora e data (Driver ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC date functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], time and date functions
- FoxPro ODBC driver [ODBC], time and date functions
- time and date functions [ODBC]
- ODBC time and date functions [ODBC]
- date functions [ODBC]
ms.assetid: c1fb63b7-af50-45d6-8dec-ae6ea7119527
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7752c1c1d5184ddb1beea26d7c35e29ea5769796
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644329"
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Funzioni data e ora (driver ODBC Visual FoxPro)
La tabella seguente elenca le funzioni di data e ora ODBC supportate per il Driver ODBC Visual FoxPro; Quando la grammatica di Visual FoxPro per la stessa funzione differisce dalla sintassi ODBC, viene elencato l'equivalente di Visual FoxPro.  
  
|Grammatica ODBC|Grammatica di Visual FoxPro|  
|------------------|---------------------------|  
|CURDATE *)*|DATA *)*|  
|FUNZIONE CURTIME *)*|TEMPO *)*|  
|Funzione DAYNAME *(date_exp)*|CDOW *(date_exp)*|  
|DAYOFMONTH (*date_exp)*|GIORNO *)*|  
|ORA *(time_exp)*||  
|MINUTO *(time_exp)*||  
|MESE *(time_exp)*||  
|MONTHNAME *(date_exp)*|CMONTH *(date_exp)*|  
|ORA *)*|DATA/ORA *)*|  
|SECONDO *(time_exp)*|SEC *(time_exp)*|  
|SETTIMANA *(date_exp)*||  
|ANNO *(date_exp)*||  
  
 Non sono supportate le funzioni di data e ora seguenti:  
  
 DAYOFYEAR *(date_exp)*  
  
 TRIMESTRE *(date_exp)*  
  
 Timestampadd non *(intervallo, integer_exp, timestamp_exp)*  
  
 Timestampdiff non *(intervallo, timestamp_exp1, timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>Sequenze di escape ODBC  
 Il driver supporta anche la sequenza di escape ODBC per i dati di data e timestamp. La sintassi della clausola di escape è come segue:  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)—  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)—  
```  
  
 In questa sintassi **1!d** indica che *valore* data nel *aaaa-mm-gg* formato e **ts** indica che *valore*  è un timestamp nel *aaaa-mm-gg hh.mm.ss*[.*f...*] formato. La sintassi abbreviata per i dati di data e timestamp è come segue:  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Ad esempio, ognuna delle seguenti affermazioni Aggiorna la tabella ALLTYPES usando la sintassi abbreviata di data e timestamp in un comando SQL UPDATE supportato:  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sulle sequenze di escape, vedere [sequenze di Escape in ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) nel *riferimento per programmatori ODBC*.
