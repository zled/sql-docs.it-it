---
title: Sottochiave traduttori ODBC | Documenti Microsoft
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
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ede16122078aa53d3eeb0799678537746e3fcf12
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-translators-subkey"></a>Sottochiave traduttori ODBC
I valori della sottochiave ODBC traduttori elencare i traduttori installati. Nella tabella seguente è illustrato il formato di questi valori.  
  
|Nome|Tipo di dati|data|  
|----------|---------------|----------|  
|*funzione di conversione desc*|REG_SZ|**Installato**|  
  
 Il *traduttore desc* nome è definito dallo sviluppatore del convertitore.  
  
 Ad esempio, si supponga che un utente ha installato un ASCII personalizzato e il convertitore di tabella codici di Microsoft® traduttore EBCDIC. I valori nella sottochiave traduttori ODBC potrebbero essere come segue:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
