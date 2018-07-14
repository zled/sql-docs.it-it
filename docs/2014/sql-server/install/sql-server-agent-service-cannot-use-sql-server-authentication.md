---
title: Servizio SQL Server Agent non è possibile usare l'autenticazione di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 263f3e865a59b215ccbfc0382958dffe5cfb518e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238261"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a>Il servizio SQL Server Agent non può utilizzare l'autenticazione di SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent supporta solo l'autenticazione di Windows quando il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent si connette a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent può accedere al database solo utilizzando l'autenticazione di Windows. Pertanto, l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent deve essere un utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Per ulteriori informazioni, vedere gli argomenti relativi alla sicurezza per l'amministrazione automatica e all'implementazione della sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento di SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
