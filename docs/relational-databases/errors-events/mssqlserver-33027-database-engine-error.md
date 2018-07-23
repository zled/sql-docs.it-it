---
title: MSSQLSERVER_33027 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e7d9b03347fb6ca83827854f4af0b75e8accc131
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37190951"
---
# <a name="mssqlserver33027"></a>MSSQLSERVER_33027
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
SQL Server non è stato in grado di usare il provider del servizio di crittografia elencato nel messaggio di errore perché SQL Server non è in grado di caricare la DLL. Il nome non è valido o la firma Authenticode è non valida.  
  
## <a name="user-action"></a>Azione dell'utente  
Verificare che il file sia presente e che SQL Server disponga dell'autorizzazione ad accedere a tale percorso. Per visualizzare altri messaggi correlati, controllare il log degli errori. In caso contrario, contattare il provider del servizio di crittografia per ulteriori informazioni.  
  
