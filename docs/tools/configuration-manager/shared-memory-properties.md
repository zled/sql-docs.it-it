---
title: Proprietà Shared Memory | Microsoft Docs
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
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
caps.latest.revision: 21
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 48cf75a64fea6b82b5417b57e431fa347d867c9d
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "42784616"
---
# <a name="shared-memory-properties"></a>Proprietà Shared Memory
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Usare la pagina **Protocollo** nella finestra di dialogo **Proprietà Shared Memory** per abilitare o disabilitare il protocollo Shared Memory. Shared Memory è il protocollo più semplice da utilizzare e non richiede la configurazione di impostazioni. Poiché i client che usano questo protocollo possono connettersi solo a un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eseguita nello stesso computer, Shared Memory non è adatto per la maggior parte delle attività del database. Utilizzare il protocollo Shared Memory per la risoluzione dei problemi quando si sospetta che gli altri protocolli siano configurati in modo non corretto.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere riavviato per abilitare o disabilitare il protocollo.  
  
## <a name="options"></a>Opzioni  
 **Abilitata**  
 I valori possibili sono **Sì** e **No**. Il protocollo Shared Memory è attivato per impostazione predefinita.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di un protocollo di rete](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Creazione di una stringa di connessione valida mediante il protocollo di memoria condivisa](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
