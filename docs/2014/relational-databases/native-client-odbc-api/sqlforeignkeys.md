---
title: SQLForeignKeys | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 20b48d67072919fe42661343ff133cd3ea1a8773
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168294"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta aggiornamento a catena ed esegue l'eliminazione tramite il meccanismo dei vincoli della chiave esterna. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce SQL_CASCADE per le colonne UPDATE_RULE e/o DELETE_RULE se l'opzione CASCADE viene specificata sulla clausola ON UPDATE e/o ON DELETE dei vincoli FOREIGN KEY. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce SQL_NO_ACTION per le colonne UPDATE_RULE e/o DELETE_RULE se l'opzione NO ACTION viene specificata sulla clausola ON UPDATE e/o ON DELETE dei vincoli FOREIGN KEY.  
  
 Quando sono presenti in altri valori non validi **SQLForeignKeys** parametro **SQLForeignKeys** restituisce SQL_SUCCESS durante l'esecuzione. **SQLFetch** restituisce SQL_NO_DATA quando in questi parametri vengono utilizzati valori non validi.  
  
 **SQLForeignKeys** può essere eseguito su un cursore server statico. Un tentativo di eseguire **SQLForeignKeys** su un cursore aggiornabile (dinamico o keyset) restituisce SQL_SUCCESS_WITH_INFO, che indica che il tipo di cursore è stato modificato.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la segnalazione di informazioni relative alle tabelle sui server collegati mediante l'accettazione di un nome composto da due parti per il *FKCatalogName* e *PKCatalogName* parametri:  *Linked_server_name*.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLForeignKeys](http://go.microsoft.com/fwlink/?LinkId=59344)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  