---
title: SQLForeignKeys | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a11cb7f1013f1ea76dbbefff1d29808ddfb4c7e9
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423101"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta aggiornamento a catena ed esegue l'eliminazione tramite il meccanismo dei vincoli della chiave esterna. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce SQL_CASCADE per le colonne UPDATE_RULE e/o DELETE_RULE se l'opzione CASCADE viene specificata sulla clausola ON UPDATE e/o ON DELETE dei vincoli FOREIGN KEY. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce SQL_NO_ACTION per le colonne UPDATE_RULE e/o DELETE_RULE se l'opzione NO ACTION viene specificata sulla clausola ON UPDATE e/o ON DELETE dei vincoli FOREIGN KEY.  
  
 Quando sono presenti in uno dei valori non validi **SQLForeignKeys** parametro **SQLForeignKeys** restituisce SQL_SUCCESS durante l'esecuzione. **SQLFetch** restituisce SQL_NO_DATA quando in questi parametri vengono utilizzati valori non validi.  
  
 **SQLForeignKeys** può essere eseguito su un cursore server statico. Un tentativo di eseguire **SQLForeignKeys** su un cursore aggiornabile (dinamico o keyset) restituisce SQL_SUCCESS_WITH_INFO, che indica che il tipo di cursore è stato modificato.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la segnalazione di informazioni relative alle tabelle sui server collegati mediante l'accettazione di un nome in due parti per il *FKCatalogName* e *PKCatalogName* parametri:  *Linked_server_name*.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLForeignKeys](http://go.microsoft.com/fwlink/?LinkId=59344)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  
