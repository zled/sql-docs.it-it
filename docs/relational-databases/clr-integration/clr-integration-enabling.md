---
title: Abilitazione dell'integrazione CLR | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
caps.latest.revision: 19
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: cf4d327ecc82f047d80eba8da709fea1fd7e82dd
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37358213"
---
# <a name="clr-integration---enabling"></a>Integrazione CLR - abilitazione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Per impostazione predefinita, la funzionalità di integrazione con Common Language Runtime (CLR) è disabilitata e deve essere abilitata per poter utilizzare gli oggetti implementati mediante l'integrazione con CLR. Per abilitare l'integrazione con CLR, usare il **clr abilitato** opzione delle **sp_configure** stored procedure [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
```sql  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 È possibile disabilitare l'integrazione CLR impostando il **clr abilitato** opzione su 0. Quando si disabilita l'integrazione con CLR, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene arrestata l'esecuzione di tutte le routine CLR e vengono scaricati tutti i domini dell'applicazione.  
  
> [!NOTE]  
>  Per abilitare l'integrazione con CLR, è necessario disporre di autorizzazione a livello server, modificare le impostazioni che è assegnata implicitamente ai membri del **sysadmin** e **serveradmin** ruoli predefiniti del server.  
  
> [!NOTE]  
>  I computer configurati con grandi quantità di memoria e con un gran numero di processori potrebbero non riuscire a caricare la funzionalità di integrazione con CLR di SQL Server all'avvio del server. Per risolvere questo problema, avviare il server usando il **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] opzione di avvio del servizio e specificare un valore di memoria sufficiente. Per altre informazioni, vedere [Opzioni di avvio del servizio del motore di database](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  L'esecuzione di CLR (Common Language Runtime) non è supportata nell'ambito dell'opzione lightweight pooling. Prima di abilitare l'integrazione con CLR, è necessario disabilitare il lightweight pooling. Per altre informazioni, vedere [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Opzione di configurazione del server clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Ruoli a livello di server](../../relational-databases/security/authentication-access/server-level-roles.md)  
  
  
