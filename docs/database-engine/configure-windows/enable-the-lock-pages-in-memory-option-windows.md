---
title: Abilitare l'opzione Blocco di pagine in memoria (Windows) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f62d2e7f2187433acdaf775d0835b1f5f7d6e5a3
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a>Abilitazione dell'opzione Blocco di pagine in memoria (Windows)
  Questi criteri di Windows determinano gli account autorizzati a usare un processo per mantenere i dati nella memoria fisica, impedendo al sistema di eseguire il paging dei dati nella memoria virtuale su disco.  
  
> [!NOTE]  
>  Bloccando le pagine in memoria è possibile migliorare le prestazioni nei casi in cui è previsto il paging della memoria su disco.  
  
 Utilizzare lo strumento Criteri di gruppo di Windows (gpedit.msc) per abilitare questi criteri per l'account utilizzato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per modificare i criteri, è necessario essere un amministratore di sistema.  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a>Per abilitare l'opzione Blocco di pagine in memoria  
  
1.  Fare clic sul menu **Start** e scegliere **Esegui**. Nella casella **Apri** digitare **gpedit.msc**.  
  
2.  Nella console **Editor Criteri di gruppo locali** espandere **Configurazione computer**, quindi **Impostazioni di Windows**.  
  
3.  Espandere **Impostazioni sicurezza**e quindi espandere **Criteri locali**.  
  
4.  Selezionare la cartella **Assegnazione diritti utente** .  
  
     I criteri verranno visualizzati nel riquadro dei dettagli.  
  
5.  Nel riquadro fare doppio clic su **Blocco di pagine in memoria**.  
  
6.  Nella finestra di dialogo **Impostazioni di sicurezza locali - Blocco di pagine in memoria** fare clic su **Aggiungi utente o gruppo**.  
  
7.  Nella finestra di dialogo **Selezione utenti, computer, account del servizio o gruppi** aggiungere un account con privilegi per l'esecuzione di sqlservr.exe.  
  
8.  Effettuare la disconnessione e nuovamente l'accesso per rendere operativa questa modifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di configurazione del server Server Memory](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  
