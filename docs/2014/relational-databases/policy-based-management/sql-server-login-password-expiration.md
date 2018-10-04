---
title: Scadenza della password di accesso di SQL server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7e3bf9da-a436-433d-847a-47c30428cad3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 04f4c766797c2563b595d4c6aa371e0b437d1197
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145741"
---
# <a name="sql-server-login-password-expiration"></a>Scadenza della password di accesso di SQL server
  Questa regola consente di controllare se è stata abilitata la scadenza della password per ogni account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se è abilitata l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e la versione del sistema operativo è precedente a [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], un utente malintenzionato potrebbe sfruttare ripetutamente una password di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nota.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 È consigliabile aggiornare il sistema operativo a [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].  
  
 Se nell'ambiente non è necessaria l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , utilizzare l'autenticazione di Windows. Per altre informazioni, vedere [Scegliere una modalità di autenticazione](../security/choose-an-authentication-mode.md).  
  
 Abilitare la scadenza delle password per tutti gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per configurare i criteri password per gli account di accesso di [, utilizzare](/sql/t-sql/statements/alter-login-transact-sql) ALTER LOGIN [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Criteri password](../security/password-policy.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
