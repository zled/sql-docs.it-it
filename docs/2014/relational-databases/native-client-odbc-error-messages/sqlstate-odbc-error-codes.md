---
title: SQLSTATE (codici di errore ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a87719c063e40befb95bc5ce61573dbae8a36325
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411320"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (codici di errore ODBC)
  SQLSTATE fornisce informazioni dettagliate sulla causa di un avviso o di un errore. Per gli errori che si verificano nei dati di origine rilevati e restituiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client esegue il mapping il numero di errore nativo restituito al codice SQLSTATE appropriato. Se un numero di errori nativi non dispone di un codice di errore ODBC per eseguire il mapping, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client restituisce SQLSTATE 42000 ("sintassi o violazione di accesso"). Per gli errori rilevati dal driver, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client genera il codice SQLSTATE appropriato.  
  
 Per ulteriori informazioni sui codici di errore di stato, vedere i seguenti argomenti:  
  
-   [Appendice A: Codici di errore ODBC](http://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [Mapping di SQLSTATE](http://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di errori e messaggi](handling-errors-and-messages.md)  
  
  
