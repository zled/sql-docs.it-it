---
title: Configurazione Winsock Proxy non supportata | Microsoft Docs
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
- Winsock proxy configuration [SQL Server]
ms.assetid: abf71f7b-8bd7-49d2-92f7-9ddf72924d8c
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3c7f0d97b2a6b0c5a853b36d9269c8237df08095
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292141"
---
# <a name="winsock-proxy-configuration-not-supported"></a>Configurazione proxy WinSock non supportata
  Il proxy Winsock non può essere configurato utilizzando [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] strumenti.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Impossibile configurare componenti WinSock con gli strumenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Azione correttiva  
 Utilizzare Microsoft Internet Security and Acceleration (ISA) Server per pubblicare un computer. Per informazioni sulla configurazione del proxy WinSock, vedere la documentazione del server proxy.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
