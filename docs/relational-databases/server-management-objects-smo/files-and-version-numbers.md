---
title: I file e numeri di versione | Documenti Microsoft
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: cfa46bd20e9094f1b83fd80933a6e9652474de1d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="files-and-version-numbers"></a>File e numeri di versione
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Tutti i necessari componenti di SQL Server Management oggetto (SMO) sono inclusi nel pacchetto Microsoft.SqlServer.SqlManagementObjects NuGet. SMO viene implementato in diversi assembly gestiti. È possibile sviluppare applicazioni SMO in un client o in un server.  

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
  
  
