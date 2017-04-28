---
title: Note sulla versione di SQL Server 2012 SP2 | Microsoft Docs
ms.prod: sql-server-2012
ms.technology: server-general
ms.custom: 
ms.date: 01/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67cb8b3e-3d82-47f4-840d-0f12a3bff565
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5e132652cc6464502785647f8a79dec5e25094c4
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-2012-sp2-release-notes"></a>SQL Server 2012 SP2 Release Notes
In queste note sulla versione sono illustrati problemi da conoscere prima di installare o risolvere i problemi di SQL Server 2012 Service Pack 2. Le note sulla versione sono disponibili solo online, non nel supporto di installazione. Sono aggiornate periodicamente, in caso di rilevamento di nuovi problemi. Per altre informazioni, vedere [Bug risolti in SQL Server 2012 Service Pack 2](http://support.microsoft.com/KB/2958429) .  
  
## <a name="choose-the-correct-file-to-download-and-install"></a>Scegliere il file corretto da scaricare e installare  
Usare la tabella seguente per identificare la posizione e il nome del file da scaricare in base alla versione attualmente installata. Le pagine per il download includono informazioni sui requisiti di sistema e istruzioni di base per l'installazione.  
  
||||  
|-|-|-|  
|**Versione attualmente installata**|**Operazione da eseguire**|**File da scaricare e installare**|  
|Installazioni a 32 bit:|||  
|Versione a 32 bit di qualsiasi edizione di SQL Server 2012|Eseguire l'aggiornamento alla versione a 32 bit di SQL Server 2012 SP2|**SQLServer2012SP2-KB2958429-**<arch>**-**<lang id>**.exe** nella [pagina di download di SQL Server 2012 SP2](http://go.microsoft.com/fwlink/?LinkID=401006)|  
|Versione a 32 bit di SQL Server 2012 RTM Express|Eseguire l'aggiornamento alla versione a 32 bit di SQL Server 2012 Express SP2|**SQLEXPR_**<arch>**_**<lang>**.msi** nella pagina di download di [SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Versione a 32 bit solo degli strumenti client e di gestibilità per SQL Server 2012 (incluso SQL Server 2012 Management Studio)|Eseguire l'aggiornamento degli strumenti client e di gestibilità alla versione a 32 bit di SQL Server 2012 SP2|**SQLEXPRWT_**<arch>**_**<lang>**.msi** nella pagina di download di [SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Versione a 32 bit di SQL Server 2012 Management Studio Express|Eseguire l'aggiornamento alla versione a 32 bit di SQL Server 2012 SP2 Management Studio Express|**SQLManagementStudio_**<arch>**_**<lang>**.msi** nella pagina di download di [SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Versione a 32 bit di qualsiasi edizione di SQL Server 2012 e versione a 32 bit degli strumenti client e di gestibilità (incluso SQL Server 2012 RTM Management Studio)|Eseguire l'aggiornamento di tutti i prodotti alla versione a 32 bit di SQL Server 2012 SP2|**SQLEXPRADV_**<arch>**_**<lang>**.msi** nella pagina di download di [SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Versione a 32 bit di uno o più strumenti di [Microsoft SQL Server 2012 RTM Feature Pack](http://www.microsoft.com/download/details.aspx?id=29065) o di [Microsoft SQL Server 2012 SP1 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkID=268266)|Eseguire l'aggiornamento degli strumenti alla versione a 32 bit di Microsoft SQL Server 2012 SP2 Feature Pack|Uno o più strumenti dalla [pagina per il download di Microsoft SQL Server 2012 SP2 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=401008)|  
|Installazioni a 64 bit:|||  
|Versione a 64 bit di qualsiasi edizione di SQL Server 2012|Eseguire l'aggiornamento alla versione a 64 bit di SQL Server 2012 SP2|SQLServer2012SP2-KB2958429-<arch>-<langid>.exe nella pagina di download di [SQL Server 2012 SP2](http://go.microsoft.com/fwlink/?LinkID=401006)|  
|Versione a 64 bit di SQL Server 2012 RTM Express|Eseguire l'aggiornamento alla versione a 64 bit di SQL Server 2012 SP2|**SQLEXPR_**<arch>**_**<lang>**.msi** nella pagina di download di [SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Versione a 64 bit solo degli strumenti client e di gestibilità per SQL Server 2012 (incluso SQL Server 2012 Management Studio)|Eseguire l'aggiornamento degli strumenti client e di gestibilità alla versione a 64 bit di SQL Server 2012 SP2|**SQLEXPRWT_**<arch>**_**<lang>**.msi** nella pagina di download di [SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Versione a 64 bit di SQL Server 2012 Management Studio Express|Eseguire l'aggiornamento alla versione a 64 bit di SQL Server 2012 SP2 Management Studio Express|**SQLManagementStudio_**<arch>**_**<lang>**.msi** nella pagina di download di [SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Versione a 64 bit di uno o più strumenti di [Microsoft SQL Server 2012 RTM Feature Pack](http://www.microsoft.com/download/details.aspx?id=29065) o di [Microsoft SQL Server 2012 SP1 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkID=268266)|Eseguire l'aggiornamento degli strumenti alla versione a 64 bit di Microsoft SQL Server 2012 SP2 Feature Pack|Uno o più strumenti dalla [pagina per il download di Microsoft SQL Server 2012 SP2 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=401008)|  
  

