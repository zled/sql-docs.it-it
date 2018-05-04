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
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a6c59901d3e784f1ab845da595c84a4e74a0129
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
