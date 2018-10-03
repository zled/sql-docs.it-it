---
title: Sottochiave ODBC Drivers | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43be1c5e75998903ff4e64fc5f4230818a873ffc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772019"
---
# <a name="odbc-drivers-subkey"></a>Sottochiave ODBC Drivers
I valori nella sottochiave ODBC driver Elenca driver installati. Nella tabella seguente viene illustrato il formato di questi valori.  
  
|nome|Tipo di dati|data|  
|----------|---------------|----------|  
|*Descrizione del driver*|REG_SZ|**installato**|  
  
 Il *-descrizione del driver* nome è definito dallo sviluppatore del driver. In genere è il nome del sistema DBMS associato al driver.  
  
 Si supponga, ad esempio, che sono stati installati i driver per SQL Server e i file di testo formattato. I valori nella sottochiave ODBC driver potrebbero essere:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
