---
title: Livello di complessità delle password di accesso di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b0862c3a-926b-490c-a37f-382e50146a3e
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fcc09a63fee8bdf59d1ba2ab320dc6c81cf96498
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065122"
---
# <a name="sql-server-login-password-strength"></a>Livello di complessità delle password di accesso di SQL Server
  Questa regola consente di controllare se è abilitata la funzionalità "Applica criteri password" di ogni account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se è abilitata l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e la versione del sistema operativo è precedente a [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], un utente malintenzionato potrebbe sfruttare ripetutamente una password di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nota.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 È consigliabile aggiornare il sistema operativo a [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].  
  
 Se nell'ambiente non è necessaria l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , utilizzare l'autenticazione di Windows.  
  
 Abilitare "Applica criteri password" per tutti gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per configurare i criteri password per gli account di accesso di [, utilizzare](/sql/t-sql/statements/alter-login-transact-sql) ALTER LOGIN [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Criteri password](../security/password-policy.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
