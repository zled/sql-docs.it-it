---
title: Modificare una sessione Eventi estesi | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: xevents
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 614b322beaf2c8e9e7c818341983f58a6228debf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="alter-an-extended-events-session"></a>Modificare una sessione Eventi estesi
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Dopo avere creato una sessione Eventi estesi, è possibile modificarla secondo necessità utilizzando la **Creazione guidata Eventi estesi di SQL Server**.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 Non è possibile modificare una destinazione per sessioni attive e inattive né modificare le configurazioni delle proprietà avanzate per una sessione attiva.  
  
 È possibile apportare le modifiche seguenti alle sessioni di eventi attive e inattive:  
  
-   Aggiungere o rimuovere eventi dalla sessione e modificare le configurazioni degli eventi, ad esempio campi evento, filtri e azioni.  
  
-   Aggiungere o rimuovere una destinazione dalla sessione eventi.  
  
-   Abilitare l'opzione **Avvia la sessione eventi all'avvio del server** .  
  
 È possibile apportare le modifiche aggiuntive seguenti a una sessioni eventi inattiva:  
  
-   Abilitare l'opzione **Rileva la relazione tra gli eventi** .  
  
-   Modificare la configurazione delle proprietà avanzate.  
  
> [!NOTE]  
>  La **Creazione guidata eventi estesi di SQL Server** non supporta la modifica delle sessioni evento.  
  
## <a name="how-to-alter-an-extended-events-session-using-the-sql-server-extended-events-wizard"></a>Modifica di una sessione Eventi estesi utilizzando la Creazione guidata Eventi estesi SQL Server  
  
-   In Esplora oggetti espandere **Gestione**, **Eventi estesi**, quindi **Sessioni**.  
  
-   Fare clic con il pulsante destro del mouse sulla sessione che si vuole modificare, quindi scegliere **Proprietà**.  
  
-   Nella finestra di dialogo **Proprietà** apportare le modifiche desiderate, quindi fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [Creare una sessione Eventi estesi tramite l'editor di query](http://msdn.microsoft.com/library/cba0e02b-b201-4863-bf1b-9164e68e5fa8)  
  
  
