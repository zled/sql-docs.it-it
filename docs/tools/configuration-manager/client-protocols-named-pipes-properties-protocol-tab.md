---
title: "Protocolli client - denominato proprietà pipe (scheda protocollo) | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
caps.latest.revision: "23"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 816c44b0498d65c6540f167537f69f5bf86fcc99
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>Protocolli client - Proprietà - Named pipe (scheda Protocollo)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzare Configuration Manager il **protocollo** scheda la **proprietà-Named Pipes** la finestra di dialogo per visualizzare o modificare la descrizione della pipe predefinita. Per connettersi a una pipe diversa, digitarne il nome nella casella **Pipe predefinita** . Per ulteriori informazioni sulle stringhe di connessione, vedere [Creating a Valid Connection String Using Named Pipes](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f).  
  
## <a name="options"></a>Opzioni  
 **Pipe predefinita**  
 Specifica la pipe predefinita usata dalla libreria di rete Named Pipes per tentare la connessione all'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in attesa su `\\.\pipe\sql\query`.  
  
 Per connettersi alla pipe predefinita, immettere `sql\query`  
  
 **Abilitata**  
 I valori possibili sono **Sì** e **No**.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di un protocollo di rete](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
