---
title: Informazioni sul Provider WMI per Gestione configurazione | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
caps.latest.revision: 21
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0f51b9f7bb736b95892716fd11955f6631d913d8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Informazioni sul provider WMI per la gestione della configurazione
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce il Provider WMI per Gestione configurazione. Consente di utilizzare WMI (Strumentazione gestione Windows) per gestire i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e impostazioni di rete server e alias del server. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servizi, le impostazioni di rete e gli alias sono rappresentati dagli oggetti WMI nello root\Microsoft\SqlServer\ComputerManagement*nn* dello spazio dei nomi del computer. Una volta stabilita una connessione con il provider WMI nel computer specificato, è possibile eseguire query su servizi, impostazioni di rete e alias utilizzando WQL o un linguaggio di scripting.  
  
 Il provider WMI è un provider di istanze Che fornisce istanze del [classi WMI](../../relational-databases/wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) e supporta le operazioni asincrone seguenti.  
  
 Recupero di istanze  
 Recupero di un'istanza di un tipo di classe specifica.  
  
 Enumerazione  
 Enumerazione di tutte le istanze di un tipo di classe.  
  
 Modifica  
 Modifica di una determinata istanza di un tipo di classe.  
  
 Le classi includono metodi che consentono la modifica delle relative proprietà.  
  
 Eliminazione  
 Rimozione di una determinata istanza di un tipo di classe.  
  
 Elaborazione di query  
 Enumerazione di istanze di un tipo di classe basata su un filtro.  
  
 Per esempi di applicazione di gestione tramite il Provider WMI per la gestione della configurazione, vedere [utilizzo di WQL e linguaggi di script con il Provider WMI per Gestione configurazione](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Per ulteriori informazioni sulla programmazione di applicazioni di gestione tramite il Provider WMI, vedere la documentazione di WMI nel [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo del Provider WMI per Gestione configurazione](../../relational-databases/wmi-provider-configuration/working-with-the-wmi-provider-for-configuration-management.md)   
 [Utilizzo di WQL e linguaggi di Scripting con il Provider WMI per Gestione configurazione](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
