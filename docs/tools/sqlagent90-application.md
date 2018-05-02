---
title: Applicazione SQLAGENT90 | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sqlagent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- starting SQL Server Agent
- sqlagent90 application
- SQL Server Agent, starting
- command prompt utilities [SQL Server], sqlagent90
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 928c16b62ce9a5bb542b81ed91cb84c1323a858b
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="sqlagent90-application"></a>sqlagent90 - applicazione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] L'applicazione **sqlagent90** avvia [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent al prompt dei comandi. In genere, è consigliabile eseguire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent da [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oppure utilizzando i metodi SQL-DMO in un'applicazione. Eseguire **sqlagent90** dal prompt dei comandi solo per attività di diagnostica su [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent o se viene richiesto dal personale del supporto tecnico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlagent90  
-c [-v] [-i instance_name]  
```  
  
## <a name="arguments"></a>Argomenti  
 **-c**  
 Indica che [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent viene eseguito dal prompt dei comandi ed è indipendente da Gestione controllo servizi di Windows. Se si utilizza **-c** , non è possibile controllare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent utilizzando l'applicazione Servizi in Strumenti di amministrazione oppure Gestione configurazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Questo argomento è obbligatorio.  
  
 **-v**  
 Indica l'esecuzione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent in modalità dettagliata e attiva la scrittura delle informazioni di diagnostica nella finestra del prompt dei comandi. Le informazioni di diagnostica sono uguali a quelle scritte nel log degli errori di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent.  
  
 **-i** *instance_name*  
 Indica che [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent si connette all'istanza denominata di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] specificata da *instance_name*.  
  
## <a name="remarks"></a>Remarks  
 Dopo il messaggio del copyright, **sqlagent90** visualizza l'output nella finestra del prompt dei comandi solo quando è specificata l'opzione **-v** . Per arrestare **sqlagent90**, premere CTRL+C al prompt dei comandi. Non chiudere la finestra del prompt dei comandi senza aver arrestato **sqlagent90**.  
  
## <a name="see-also"></a>Vedere anche  
 [Automatizzazione delle attività amministrative &#40;SQL Server Agent&#41;](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)  
  
  
