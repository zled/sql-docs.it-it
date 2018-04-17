---
title: Origine dati specifica sottochiavi | Documenti Microsoft
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
- data source specification subkeys [ODBC]
- registry entries for data sources [ODBC], data source specification subkeys
- subkeys [ODBC], data source specification subkeys
ms.assetid: d7e88a07-e6ab-4258-a45d-1ca21234fbec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5f3080d85b2c01491d94ecb75b956d6c67bc061b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="data-source-specification-subkeys"></a>Sottochiavi di specifica origine dati
Ogni origine dati elencate nella sottochiave origini dati ODBC dispone di una sottochiave propri. Questa sottochiave ha lo stesso nome come valore corrispondente nella sottochiave origini dati ODBC. I valori in questa sottochiave è necessario elencare la DLL del driver e possono elencare una descrizione dell'origine dati. Se il driver supporta funzioni di conversione, i valori possono elencare il nome di una funzione di conversione predefinita, la DLL di conversione predefinita e l'opzione di conversione predefinita. I valori possono inoltre essere elencate altre informazioni richieste dal driver per la connessione all'origine dati. Ad esempio, il driver potrebbe richiedere un nome del server, nome del database o nome dello schema.  
  
 I formati dei valori vengono visualizzati nella tabella seguente. È necessario solo il valore di Driver.  
  
|Nome|Tipo di dati|data|  
|----------|---------------|----------|  
|Description|REG_SZ|*description*|  
|Driver|REG_SZ|*driver-DLL-path*|  
|TranslationDLL|REG_SZ|*funzione di conversione-DLL-path*|  
|TranslationName|REG_SZ|*nome di funzione di conversione*|  
|TranslationOption|REG_SZ|*opzione di conversione*|  
|*OPT-nome-valore*|*OPT-tipo di valore*|*dati di valore OPT*|  
  
 Si supponga, ad esempio, il driver SQL Server richiede il nome del server e un flag per OEM per la conversione ANSI e definisce i valori di Server e non vengono per questi. Si supponga inoltre che l'origine dati di inventario utilizza il convertitore di tabella codici di Microsoft® per convertire tra le tabelle codici multilingue (850) Windows® latino 1 (1250). I valori nella sottochiave inventario potrebbero essere come segue:  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
