---
title: Named pipe Properties | Documenti Microsoft
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
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6122004c46c36f21d2b301e70be91b26fa06c701
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="named-pipes-properties"></a>Proprietà Named Pipes
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Utilizzare il **protocollo**pagina il **proprietà-Named Pipes** la finestra di dialogo per visualizzare o modificare la named pipe su cui [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in ascolto, quando si utilizza il protocollo Named Pipes.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere riavviato per abilitare o disabilitare il protocollo oppure modificare la named pipe.  
  
## <a name="options"></a>Opzioni  
 **Abilitata**  
 I valori possibili sono **Sì** e **No**.  
  
 **Nome pipe**  
 Specifica la named pipe sulla quale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resta in attesa. Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resta in attesa su `\\.\pipe\sql\query` per l'istanza predefinita e su `\\.\pipe\MSSQL$<instancename>\sql\query` per un'istanza denominata. La lunghezza massima del campo è 2047 caratteri.  
  
## <a name="creating-an-alternate-named-pipe"></a>Creazione di una named pipe alternativa  
 Per modificare la named pipe, digitare il nome della nuova pipe nella casella **Nome pipe** e quindi arrestare e riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Poiché è noto che **sql\query** è la named pipe usata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], modificare la pipe può risultare utile per ridurre il rischio di attacco da parte di programmi dannosi.  
  
### <a name="example"></a>Esempio  
 Digitare **\\\\.\pipe\unit\app** per impostare l'attesa sulla pipe **unit\app** .  
  
 Digitare **\\\\.\pipe\acct** per impostare l'attesa sulla pipe **acct** .  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitare o disabilitare un protocollo di rete del server](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [Scelta di un protocollo di rete](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Creazione di una stringa di connessione valida tramite named pipe](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
