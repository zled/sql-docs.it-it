---
title: MSSQLSERVER_33129 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 33129 (Database Engine error)
ms.assetid: 83b5f368-f1a1-4a40-9bb6-c77e2dec690f
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d834ce29e5b21445cfa53d0ef59a5893356e74d8
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver33129"></a>MSSQLSERVER_33129
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|33129|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SEC_CANNOT_DISABLE_WIN_GROUP|  
|Testo del messaggio|Non è possibile utilizzare ALTER_LOGIN con l'argomento DISABLE per negare l'accesso a un gruppo di Windows.|  
  
## <a name="explanation"></a>Spiegazione  
Questo messaggio viene visualizzato se si tenta di disabilitare l'accesso di un Gruppo di Windows.  
  
## <a name="user-action"></a>Azione dell'utente  
Impossibile disabilitare l'accesso di un Gruppo di Windows. Per rimuovere temporaneamente l'autorizzazione di accesso concessa a un Gruppo di Windows, revocare l'autorizzazione CONNECT dell'accesso per il Gruppo di Windows. Gli utenti di Windows potrebbero continuare a disporre dell'accesso tramite il proprio accesso individuale o un altro Gruppo di Windows. L'esempio seguente revoca l'autorizzazione di connessione al gruppo Contabilità del dominio WESTCOAST.  
  
```Transact-SQL  
REVOKE CONNECT TO [WESTCOAST\Accounting];  
```  
  

