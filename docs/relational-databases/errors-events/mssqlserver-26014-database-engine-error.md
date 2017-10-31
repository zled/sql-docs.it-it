---
title: MSSQLSERVER_26014 | Microsoft Docs
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
- 26014 (Database Engine error)
ms.assetid: e2b0dfc7-0681-4e5d-8875-1d5f63534086
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a71f672ec2210c212e6e66221164224376ee4c89
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver26014"></a>MSSQLSERVER_26014
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|26014|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SNI_SSL_USER_CERT_FAILURE|  
|Testo del messaggio|Impossibile caricare il certificato specificato dall'utente [Cert Hash(sha1) "%hs"]. Il server non accetterà la connessione. Verificare che il certificato sia installato in modo corretto. Vedere la sezione relativa alla configurazione dei certificati per l'utilizzo con SSL nella documentazione online.|  
  
## <a name="explanation"></a>Spiegazione  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è stato eseguito un tentativo di caricare il certificato indicato nel messaggio, ma l'operazione non è riuscita. Prima che in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia possibile utilizzare questo certificato, è necessario risolvere il problema.  
  
Alcune cause possibili dell'errore sono le seguenti:  
  
-   È possibile che il certificato sia stato spostato o eliminato.  
  
-   Se l'account di accesso utilizzato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è stato modificato, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbero non essere disponibili le autorizzazioni per accedere al certificato.  
  
-   Il certificato potrebbe essere scaduto.  
  
## <a name="user-action"></a>Azione dell'utente  
Verificare che certificato indicato nel messaggio esista nel sistema, che sia accessibile e che sia valido per l'utilizzo.  
  

