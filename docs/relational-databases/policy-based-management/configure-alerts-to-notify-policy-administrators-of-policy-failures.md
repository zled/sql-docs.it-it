---
title: Configurare avvisi per notificare agli amministratori eventuali errori dei criteri| Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, configure alerts
ms.assetid: e8e60159-d5b0-49d5-91f3-af8e9cb994c1
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 44565d371ca75d4d707274b90d52794473f63a72
ms.lasthandoff: 04/11/2017

---
# <a name="configure-alerts-to-notify-policy-administrators-of-policy-failures"></a>Configurare avvisi per notificare agli amministratori eventuali errori dei criteri
  Se si verifica una violazione quando i criteri di gestione basata su criteri vengono eseguiti in una delle tre modalità di valutazione automatiche, viene scritto un messaggio nel registro eventi. Per ricevere una notifica relativa all'avvenuta scrittura del messaggio nel registro eventi, è possibile creare un avviso per rilevare il messaggio ed eseguire un'azione. L'avviso dovrà rilevare i messaggi come indicato nella tabella seguente.  
  
|Modalità di esecuzione|Numero di messaggio|  
|--------------------|--------------------|  
|Su modifica: impedisci esecuzione<br /><br /> (se automatica)|34050|  
|Su modifica: impedisci esecuzione<br /><br /> (se Su richiesta)|34051|  
|Su pianificazione|34052|  
|Su modifica|34053|  
  
 Per configurare un avviso per rispondere ai messaggi di errore relativi alla gestione basata su criteri, vedere gli argomenti seguenti:  
  
-   [Creazione di un operatore](http://msdn.microsoft.com/library/1359d790-5905-4927-a208-e7155e7768a2)  
  
-   [Creazione di un avviso utilizzando un numero di errore](http://msdn.microsoft.com/library/03dd7fac-5073-4f86-babd-37e45a86023c)  
  
-   [Assegnazione di avvisi a un operatore](http://msdn.microsoft.com/library/aa818155-6fa2-4565-a09f-5c7e31c89754)  
  
## <a name="permissions"></a>Autorizzazioni  
 Quando i criteri vengono valutati su richiesta, vengono eseguiti nel contesto di sicurezza dell'utente. Per poter scrivere nel log degli errori, l'utente deve disporre di autorizzazioni ALTER TRACE o deve essere un membro del ruolo predefinito del server sysadmin. I criteri valutati da un utente che dispone di privilegi di livello inferiore non verranno scritti nel registro eventi e non genereranno un avviso.  
  
 Le modalità di esecuzione automatiche possono essere eseguite solo da membri del ruolo sysadmin. Tale ruolo consente la scrittura dei criteri nel log degli errori e la generazione di un avviso.  
  
## <a name="additional-considerations-about-alerts"></a>Considerazioni aggiuntive sugli avvisi  
 Tenere presente le considerazioni aggiuntive seguenti relative agli avvisi:  
  
-   Gli avvisi vengono generati solo per i criteri abilitati. Poiché i criteri **Su richiesta** non possono essere abilitati, non vengono generati avvisi per i criteri eseguiti su richiesta.  
  
-   Se l'azione che si desidera eseguire include l'invio di un messaggio di posta elettronica, è necessario configurare un account di posta elettronica. È consigliabile utilizzare Posta elettronica database. Per altre informazioni su come configurare Posta elettronica database, vedere [Creare un account di Posta elettronica database](../../relational-databases/database-mail/create-a-database-mail-account.md).  
  
  
