---
title: MSSQLSERVER_33027 | Microsoft Docs
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
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8d7e546f593d1a54c2787da74cfe34502598a0b3
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver33027"></a>MSSQLSERVER_33027
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|33027|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SEC_CRYPTOPROV_CANTLOADDLL|  
|Testo del messaggio|Impossibile caricare il provider del servizio di crittografia '%.*ls' a causa di una firma Authenticode o un percorso file non valido. Controllare i messaggi precedenti per altri errori.|  
  
## <a name="explanation"></a>Spiegazione  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è stato in grado di usare il provider del servizio di crittografia elencato nel messaggio di errore perché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in grado di caricare la DLL. Il nome non è valido o la firma Authenticode è non valida.  
  
## <a name="user-action"></a>Azione dell'utente  
Verificare che il file sia presente e che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponga dell'autorizzazione ad accedere a tale percorso. Per visualizzare altri messaggi correlati, controllare il log degli errori. In caso contrario, contattare il provider del servizio di crittografia per ulteriori informazioni.  
  

