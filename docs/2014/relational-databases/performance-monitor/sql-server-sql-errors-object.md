---
title: Oggetto SQL Errors di SQL Server | Microsoft Docs
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
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5e3bf1e3113f64e68933c27a23e58f21f0cd6553
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064227"
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
  
  