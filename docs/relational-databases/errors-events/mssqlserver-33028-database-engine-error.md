---
title: MSSQLSERVER_33028 | Microsoft Docs
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
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c49c2798ec9f9cbf58c9193bdb1b9289a38697cb
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver33028"></a>MSSQLSERVER_33028
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|33028|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SEC_CRYPTOPROV_CANTOPENSESSION|  
|Testo del messaggio|Impossibile aprire la sessione per % S_MSG '%.* ls.' Codice di errore del provider: %d.|  
  
## <a name="explanation"></a>Spiegazione  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è stato in grado di aprire il provider del servizio di crittografia elencato nel messaggio di errore. Il codice di errore è stato indicato dal provider del servizio di crittografia. Per ulteriori informazioni sull'errore, potrebbe essere necessario contattare il provider.  
  
|Codice di errore|Description|  
|--------------|---------------|  
|0|Esito positivo. Nessun errore.|  
|1|Esito negativo. Si verificato un errore non specificato o imprevisto. Non sono disponibili informazioni aggiuntive.|  
|2|Buffer insufficiente. Impossibile allocare lo spazio per il provider del servizio di crittografia.|  
|3|Non supportato. Il provider di crittografia non è supportato da questa versione. Selezionare un altro provider del servizio di crittografia.|  
|4|Non trovato. Il provider del servizio di crittografia specificato non è presente o non si dispone dell'autorizzazione per accedere ai file.|  
|5|Errore di autorizzazione. Viene visualizzato se si specifica una password o un nome utente errati durante la creazione della credenziale o quando la credenziale non esiste.|  
|6|Argomento non valido. Un argomento non valido è stato passato al provider del servizio di crittografia.|  
  
## <a name="user-action"></a>Azione dell'utente  
Risolvere l'errore o contattare il provider del servizio di crittografia per ulteriori informazioni.  
  
