---
title: Opzione di configurazione del server filestream access level | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 55fd553670edcb4edfe6c531c13d922433b84ddd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37318921"
---
# <a name="filestream-access-level-server-configuration-option"></a>Opzione di configurazione del server filestream access level
  Utilizzare l'opzione filestream_access_level per modificare il livello di accesso di FILESTREAM per l'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Prima che questa opzione abbia effetto, è necessario abilitare le impostazioni dell'amministrazione di Windows per FILESTREAM. È possibile abilitare queste impostazioni durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure tramite Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|valore|Definizione|  
|-----------|----------------|  
|0|Disabilita il supporto di FILESTREAM per l'istanza corrente.|  
|1|Abilita FILESTREAM per l'accesso [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|2|Abilita l'accesso tramite flusso [!INCLUDE[tsql](../../includes/tsql-md.md)] e Win32 per FILESTREAM.|  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione del Motore di database - Filestream](../../sql-server/install/database-engine-configuration-filestream.md)   
 [Abilitare e configurare FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  
