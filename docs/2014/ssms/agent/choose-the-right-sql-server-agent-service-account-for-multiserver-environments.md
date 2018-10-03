---
title: Scegliere l'Account di servizio Right SQL Server Agent per ambienti Multiserver | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ed13a65b6cecee8d45235368f3b6f8f120f64ede
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069241"
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>Scegliere l'account di servizio SQL Server Agent adatto ad ambienti multiserver
  L'account di Windows scelto per il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent può influenzare il comportamento di un ambiente multiserver, come illustrato di seguito:  
  
-   Se si esegue il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent con un account che non appartiene al gruppo Administrators locale di Windows, è possibile che l'integrazione dei server di destinazione nei server master abbia esito negativo. In questo caso, verrà visualizzato il messaggio di errore seguente:  
  
     "Operazione di integrazione non riuscita."  
  
     Per risolvere il problema, riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
-   Quando il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent viene eseguito con l'account di sistema locale, le operazioni tra server master e server di destinazione sono supportate solo se entrambi risiedono nello stesso computer. Se si utilizza questa configurazione, quando si integrano i server di destinazione in un server master, verrà visualizzato il seguente messaggio:  
  
     "Verifica che l'account di avvio dell'agente per *<nome_computer_server_destinazione>* disponga dei diritti per l'accesso come server di destinazione".  
  
     Questo messaggio può essere ignorato. L'operazione di integrazione verrà completata correttamente.  
  
 Per informazioni su come selezionare l'account di avvio del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, vedere [Selezionare un account per il servizio SQL Server Agent](select-an-account-for-the-sql-server-agent-service.md).  
  
  
