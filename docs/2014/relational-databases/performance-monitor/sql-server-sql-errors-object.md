---
title: Oggetto SQL Errors di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 39124cefec0dafb921c13209adfb46e6658e1546
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43814627"
---
# <a name="sql-server-sql-errors-object"></a>Oggetto Errori SQL di SQL Server
  L'oggetto **SQLServer:Errori SQL** di Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include contatori che consentono di monitorare **Errori SQL**.  
  
 Nella tabella seguente sono illustrati i contatori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Errori SQL** .  
  
|Contatori dell'oggetto Errori SQL di SQLServer|Description|  
|------------------------------------|-----------------|  
|**Errori/sec**|Numero di errori/sec|  
  
 Per ogni contatore nell'oggetto sono disponibili le istanze seguenti:  
  
|Elemento|Definizione|  
|----------|----------------|  
|**_Total**|Informazioni relative a tutti gli errori.|  
|**DB Offline Errors**|Tiene traccia degli errori gravi che obbligano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a impostare il database corrente come offline.|  
|**Info Errors**|Informazioni relative a messaggi di errore di tipo informativo che non provocano errori.|  
|**Kill Connection Errors**|Tiene traccia degli errori gravi che obbligano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a terminare la connessione corrente.|  
|**User Errors**|Informazioni sugli errori dell'utente.|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](monitor-resource-usage-system-monitor.md)  
  
  
