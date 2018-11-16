---
title: Proprietà named pipe | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 1b409e99fd8879269d68fd68686aceaf5dbf0515
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51657161"
---
# <a name="named-pipes-properties"></a>Proprietà Named Pipes
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  La pagina **Protocollo**della finestra di dialogo **Proprietà - Named Pipes** consente di visualizzare o modificare la named pipe sulla quale [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resta in attesa quando è in uso il protocollo Named Pipes.  
  
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
 [Scelta di un protocollo di rete](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Creazione di una stringa di connessione valida tramite named pipe](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
