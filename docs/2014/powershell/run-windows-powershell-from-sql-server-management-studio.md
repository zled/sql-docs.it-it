---
title: Eseguire Windows PowerShell da SQL Server Management Studio| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cc952b88a4828ae672bd6cee2cad0754f0ef6eaf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205241"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a>Esecuzione di Windows PowerShell da SQL Server Management Studio
  È possibile avviare sessioni di Windows PowerShell da **Esplora oggetti** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Avvia Windows PowerShell, carica il `sqlps` modulo e imposta il contesto del percorso per il nodo associato nel **Esplora oggetti** struttura ad albero.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 Quando si specifica l'esecuzione di PowerShell per un oggetto in **Esplora oggetti**, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] inizia una sessione di Windows PowerShell in cui sono stati caricati e registrati gli snap-in PowerShell di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Il percorso della sessione è preimpostato sulla posizione dell'oggetto su cui si è fatto clic con il pulsante destro del mouse in Esplora oggetti. Ad esempio, facendo clic con il pulsante destro del mouse sull'oggetto del database [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] in Esplora oggetti e selezionando **Avvia PowerShell**, il percorso di PowerShell viene impostato come segue:  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="run-powershell"></a>Esecuzione di PowerShell  
 **Per eseguire PowerShell da SQL Server Management Studio**  
  
1.  Aprire **Esplora oggetti**.  
  
2.  Passare al nodo corrispondente all'oggetto desiderato.  
  
3.  Fare clic con il pulsante destro del mouse sull'oggetto e selezionare **Avvia PowerShell**.  
  
## <a name="permissions"></a>Permissions  
 In caso di apertura da [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], PowerShell non viene eseguito con privilegi di amministratore che possono impedire alcune attività quali chiamate a WMI.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
