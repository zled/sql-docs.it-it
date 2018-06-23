---
title: Abilitazione dell'integrazione CLR | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 15ad6087fc711de1ab818b10d591cd48512bb9a3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156717"
---
# <a name="enabling-clr-integration"></a>Abilitazione dell'integrazione con CLR
  Per impostazione predefinita, la funzionalità di integrazione con Common Language Runtime (CLR) è disabilitata e deve essere abilitata per poter utilizzare gli oggetti implementati mediante l'integrazione con CLR. Per abilitare l'integrazione con CLR, usare il **clr abilitato** opzione del **sp_configure** stored procedure:  
  
```  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 È possibile disabilitare l'integrazione con CLR impostando il **clr abilitato** opzione su 0. Quando si disabilita l'integrazione con CLR, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene arrestata l'esecuzione di tutte le routine CLR e vengono scaricati tutti i domini dell'applicazione.  
  
> [!NOTE]  
>  Per abilitare l'integrazione con CLR, è necessario disporre di server a livello dell'autorizzazione ALTER SETTINGS, che viene assegnata implicitamente ai membri del **sysadmin** e **serveradmin** predefiniti del server.  
  
> [!NOTE]  
>  I computer configurati con grandi quantità di memoria e con un gran numero di processori potrebbero non riuscire a caricare la funzionalità di integrazione con CLR di SQL Server all'avvio del server. Per risolvere questo problema, avviare il server utilizzando il **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] opzione di avvio del servizio e specificare un valore di memoria sufficiente. Per altre informazioni, vedere [Opzioni di avvio del servizio del motore di database](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  L'esecuzione di CLR (Common Language Runtime) non è supportata nell'ambito dell'opzione lightweight pooling. Prima di abilitare l'integrazione con CLR, è necessario disabilitare il lightweight pooling. Per altre informazioni, vedere [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Opzione di configurazione del server clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)   
 [Ruoli a livello di server](../security/authentication-access/server-level-roles.md)  
  
  
