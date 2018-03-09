---
title: Modello a oggetti SMO | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3b6cce76b87a3adaf31dea029b521fbef5cdb37d
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="smo-object-model"></a>Modello a oggetti SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Il modello a oggetti SMO è costituito da una gerarchia di oggetti. L'oggetto <xref:Microsoft.SqlServer.Management.Smo.Server> rappresenta l'oggetto di livello principale e tutti gli oggetti classe di istanza si trovano all'interno dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Server>.  
  
 La classe <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> è una classe di livello principale con una gerarchia di oggetti distinta. Il <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> oggetto [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servizi e le impostazioni di rete disponibili tramite il Provider WMI.  
  
 Oltre agli oggetti <xref:Microsoft.SqlServer.Management.Smo.Server> e <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>, sono disponibili diverse classi di utilità che rappresentano attività e operazioni, ad esempio <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup> o <xref:Microsoft.SqlServer.Management.Smo.Restore>  
  
 Il modello a oggetti SMO è costituito da diversi spazi dei nomi. Per altre informazioni, vedere [Spazio dei nomi SMO](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Diagramma del modello a oggetti SMO](../../relational-databases/server-management-objects-smo/smo-object-model-diagram.md)   
 [Spazi dei nomi SMO](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md)   
 [Concetti relativi al provider WMI per Gestione configurazione](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
