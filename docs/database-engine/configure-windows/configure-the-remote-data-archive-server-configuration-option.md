---
title: Configurare l'opzione di configurazione del server remote data archive | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b5817b5a-f39a-4faf-b11e-a47b54fd9f32
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 60b994027d5b135e3e1008992d159c3941ea970e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32863566"
---
# <a name="configure-the-remote-data-archive-server-configuration-option"></a>Configurare l'opzione di configurazione del server remote data archive
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Usare l'opzione **remote data archive** per specificare se i database e le tabelle nel server possono essere abilitati per l'estensione. Per ulteriori informazioni, vedere [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 L'opzione **remote data archive** può avere i valori seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|0|I database e le tabelle nel server non possono essere abilitati per l'estensione.|  
|1|I database e le tabelle nel server possono essere abilitati per l'estensione.|  
  
 L'esecuzione di **sp_configure** per impostare il valore dell'opzione **remote data archive** richiede autorizzazioni sysadmin o serveradmin.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente visualizza per prima l'impostazione corrente dell'opzione **remote data archive** . L'esempio abilita quindi l'opzione **remote data archive** impostandone il valore su 1.  
  
```  
EXEC sp_configure 'remote data archive';  
GO  
EXEC sp_configure 'remote data archive' , '1';  
GO  
RECONFIGURE;  
GO  
```  
  
 Per disabilitare l'opzione, impostare il valore su 0.  
  
## <a name="see-also"></a>Vedere anche  
 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Estensione database](../../sql-server/stretch-database/stretch-database.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
