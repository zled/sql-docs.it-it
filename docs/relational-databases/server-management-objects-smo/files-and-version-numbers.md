---
title: I file e numeri di versione | Documenti Microsoft
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a81f6f2228ac9f91dbc5fd401fcda16fb249989d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="files-and-version-numbers"></a>File e numeri di versione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Tutti i necessari componenti di SQL Server Management oggetto (SMO) sono inclusi nel pacchetto Microsoft.SqlServer.SqlManagementObjects NuGet. SMO viene implementato in diversi assembly gestiti. È possibile sviluppare applicazioni SMO in un client o in un server.  

>>[!Important]
La versione del file degli assembly SMO viene visualizzata come principale. **0**. Build.Revision. Ma la versione di assembly incorporato è principale. **100**. Build.Revision. Questa operazione viene eseguita per mantenere la versione di SMO in ogni applicazione separata in modo non influenza gli aggiornamenti a uno degli altri.
>>
>>Per questo motivo è consigliabile **non** installano queste versioni degli assembly in Global Assembly Cache (GAC). Ciò potrebbe causare altre applicazioni, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio, l'interruzione. 
  
|File|Description|  
|-----------|-----------------|  
|Microsoft.SqlServer.ConnectionInfo.dll|Contiene supporto per la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Microsoft.SqlServer.ServiceBrokerEnum.dll|Contiene supporto per la programmazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker. È richiesto solo in programmi che accedono a Service Broker.|  
|Microsoft.SqlServer.Smo.dll|Contiene la maggior parte delle classi SMO.|  
|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|Contiene il supporto per le classi SMO.|  
|Microsoft.SqlServer.WmiEnum.dll|Contiene le classi del provider Strumentazione gestione Windows (WMI, Windows Management Instrumentation). È richiesto solo per programmi che utilizzano le classi del Provider WMI.|  
|Microsoft.SqlServer.RegSvrEnum.dll|Contiene le classi del server registrato. È richiesto solo per programmi che utilizzano le classi del server registrato.|  
  
  
