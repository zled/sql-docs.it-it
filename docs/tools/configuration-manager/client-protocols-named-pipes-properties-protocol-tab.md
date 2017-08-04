---
title: "Protocolli client - denominato proprietà pipe (scheda protocollo) | Documenti Microsoft"
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
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 33d801033e2431f465e97502dcabf37f6a9c4847
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# Protocolli client - Proprietà - Named pipe (scheda Protocollo)
  In Gestione configurazione [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzare la scheda **Protocollo** della finestra di dialogo delle proprietà **Named Pipes** per visualizzare o modificare la descrizione della pipe predefinita. Per connettersi a una pipe diversa, digitarne il nome nella casella **Pipe predefinita** . Per ulteriori informazioni sulle stringhe di connessione, vedere [Creating a Valid Connection String Using Named Pipes](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f).  
  
## Opzioni  
 **Pipe predefinita**  
 Specifica la pipe predefinita usata dalla libreria di rete Named Pipes per tentare la connessione all'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in attesa su `\\.\pipe\sql\query`.  
  
 Per connettersi alla pipe predefinita, immettere `sql\query`  
  
 **Abilitata**  
 I valori possibili sono **Sì** e **No**.  
  
## Vedere anche  
 [Scelta di un protocollo di rete](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
