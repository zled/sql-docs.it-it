---
title: Proprietà Shared Memory | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 4f09f4502f11d49dc9aa54a7f708fda065d23094
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51660410"
---
# <a name="shared-memory-properties"></a>Proprietà Shared Memory
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Usare la pagina **Protocollo** nella finestra di dialogo **Proprietà Shared Memory** per abilitare o disabilitare il protocollo Shared Memory. Shared Memory è il protocollo più semplice da utilizzare e non richiede la configurazione di impostazioni. Poiché i client che usano questo protocollo possono connettersi solo a un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eseguita nello stesso computer, Shared Memory non è adatto per la maggior parte delle attività del database. Utilizzare il protocollo Shared Memory per la risoluzione dei problemi quando si sospetta che gli altri protocolli siano configurati in modo non corretto.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere riavviato per abilitare o disabilitare il protocollo.  
  
## <a name="options"></a>Opzioni  
 **Abilitata**  
 I valori possibili sono **Sì** e **No**. Il protocollo Shared Memory è attivato per impostazione predefinita.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di un protocollo di rete](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Creazione di una stringa di connessione valida mediante il protocollo di memoria condivisa](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
