---
title: Requisiti dell'account per l'aggiornamento a SQL Server 2008 in un controller di dominio del servizio | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
caps.latest.revision: 16
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9cc2ec39bee7f9a64d75ccf4753220f69693155b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301661"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a>Requisiti dell'account del servizio per l'aggiornamento a SQL Server 2008 in un controller di dominio
  Preparazione aggiornamento ha rilevato un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione con un account di servizio di rete o servizio locale in un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] controller di dominio. Se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è installato in un controller di dominio [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], non è possibile eseguire i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con i privilegi dell'account Servizio locale o Servizio di rete.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Assicurarsi che tutti gli account del servizio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] siano assegnati ad account Dominio o Sistema locale. Se questa modifica non viene eseguita prima dell'aggiornamento, l'installazione si bloccherà. Fanno eccezione i servizi writer SQL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e Active Directory Helper degli account del servizio, per i quali l'utilizzo dell'account servizio di rete è specificato a livello di codice e non può essere modificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
