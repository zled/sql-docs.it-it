---
title: Opzioni di configurazione del server SMO e DMO XPs | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b8cf91274210e10fa4e46f2c4b9bd90486a28e6b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47651269"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>Opzioni di configurazione del server SMO e DMO XPs
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  L'opzione SMO and DMO XPs consente di abilitare le stored procedure estese SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object) nel server.  
  
 Si noti che, a partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], DMO è stato rimosso da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 I valori possibili sono illustrati nella tabella seguente:  
  
|valore|Significato|  
|-----------|-------------|  
|0|Le stored procedure estese SMO non sono disponibili.|  
|1|Le stored procedure estese SMO sono disponibili. Impostazione predefinita.|  
  
 L'impostazione diventa immediatamente effettiva.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono abilitate le stored procedure estese SMO.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida alla programmazione di SQL Server Management Objects &#40;SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
