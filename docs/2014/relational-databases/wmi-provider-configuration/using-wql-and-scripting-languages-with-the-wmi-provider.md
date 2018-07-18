---
title: Utilizzo di WQL e linguaggi di Scripting con il Provider WMI per gestione della configurazione | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
caps.latest.revision: 17
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 7a55fc42e5186615dbe3e455668eb8cc5f7c199c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202881"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider-for-configuration-management"></a>Utilizzo di WQL e di linguaggi di scripting con il provider WMI per la gestione della configurazione
  Le applicazioni di gestione accedono a servizi e impostazioni di rete di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando il provider di Strumentazione gestione Windows (WMI, Windows Management Instrumentation) per gli oggetti di gestione della configurazione in due modi diversi:  
  
-   Utilizzando un editor WQL o un strumento di query, ad esempio WBEMTest.exe, per eseguire una query sul set di oggetti con WQL.  
  
-   Utilizzando un linguaggio di scripting, ad esempio VBScript.  
  
 In alternativa, i servizi e le impostazioni di rete di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono essere gestiti a livello di programmazione utilizzando oggetti gestiti WMI in SMO. Per ulteriori informazioni sulla programmazione WMI gestiti gli oggetti, vedere [la gestione dei servizi e le impostazioni di rete dal Provider WMI utilizzando](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
 È possibile accedere al provider WMI per la gestione della configurazione utilizzando Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console. Per altre informazioni sull'accesso al provider WMI da un'interfaccia utente, vedere [gestione dei servizi di argomenti relativi alle procedure &#40;Gestione configurazione SQL Server&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Accedere al Provider WMI per Gestione configurazione usando WQL](access-wmi-provider-for-configuration-management-using-wql.md)   
 [Modificare le proprietà avanzate del servizio SQL Server usando VBScript](access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
