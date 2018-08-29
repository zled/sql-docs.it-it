---
title: Protocolli client - Proprietà Named pipe (scheda Protocollo) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
caps.latest.revision: 23
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: fa9108c526fc957a77938200a881535cf2afafa9
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "42785527"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>Protocolli client - Proprietà - Named pipe (scheda Protocollo)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  In Gestione configurazione [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzare la scheda **Protocollo** della finestra di dialogo delle proprietà **Named Pipes** per visualizzare o modificare la descrizione della pipe predefinita. Per connettersi a una pipe diversa, digitarne il nome nella casella **Pipe predefinita** . Per ulteriori informazioni sulle stringhe di connessione, vedere [Creating a Valid Connection String Using Named Pipes](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f).  
  
## <a name="options"></a>Opzioni  
 **Pipe predefinita**  
 Specifica la pipe predefinita usata dalla libreria di rete Named Pipes per tentare la connessione all'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in ascolto su: `\\.\pipe\sql\query`  
  
 Per connettersi alla pipe predefinita, immettere `sql\query`  
  
 **Abilitata**  
 I valori possibili sono **Sì** e **No**.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di un protocollo di rete](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
