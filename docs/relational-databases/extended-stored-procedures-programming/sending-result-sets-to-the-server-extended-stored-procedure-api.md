---
title: L'invio di set di risultati al Server (API Stored Procedure esteso) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0dd49eba42bd735430bd73f244e76a13c8315806
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>Invio di set di risultati al server (API delle stored procedure estese)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilizzare invece la funzionalità di integrazione con CLR.  
  
 Durante l'invio di un set di risultati a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la stored procedure estesa deve chiamare l'API appropriata, come indicato di seguito:  
  
-   Il **srv_sendmsg** funzione può essere chiamata in qualsiasi ordine prima o dopo tutte le righe (se presenti) sono state inviate con **srv_sendrow**. Tutti i messaggi devono essere inviati al client prima che lo stato di completamento venga inviato con **srv_senddone**.  
  
-   La funzione **srv_sendrow** viene chiamata una volta per ogni riga inviata al client. Tutte le righe devono essere inviate al client prima che qualsiasi messaggio, i valori di stato o stato di completamento venga inviato con **srv_sendmsg**, **srv_status** argomento di **srv_pfield**, o **srv_senddone**.  
  
-   L'invio di una riga che non ha tutte le colonne definite con **srv_describe** fa sì che l'applicazione generi un messaggio di errore informativo e restituisca FAIL al client. In questo caso, la riga non viene inviata.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di stored procedure estese](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)  
  
  
