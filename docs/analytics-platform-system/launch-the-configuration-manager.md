---
title: Avviare Gestione configurazione (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b914ba9a-e4ec-4750-934a-c447fc8909e3
caps.latest.revision: "22"
ms.openlocfilehash: 98ae90d198b4a1b68e1b72305721611a8efa30ff
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="launch-the-configuration-manager"></a>Avviare Gestione configurazione
In questo argomento vengono fornite istruzioni per l'avvio di **Configuration Manager** per l'applicazione di sistema della piattaforma Analitica.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
### <a name="prerequisites"></a>Prerequisiti  
Il sistema di piattaforma Analitica**Configuration Manager** può essere eseguito solo dall'amministratore del dominio applicazione. Per eseguire questo strumento, è necessario specificare la password per l'amministratore del dominio applicazione. Per creare altri amministratori di punti di accesso, vedere [creare un amministratore di dominio APS &#40; APS &#41; ](create-an-aps-domain-administrator-aps.md).  
  
## <a name="Accessing"></a>Avviare lo strumento di Configuration Manager  
Per eseguire Gestione configurazione, utilizzare Desktop remoto per connettersi al nodo di controllo PDW (***PDW_region*-CTL01**) nodo e accedere come *appliance_domain* **\Administrator**. Quando si avvia il **Configuration Manager** di programma, utilizzare il **Esegui come amministratore** opzione per verificare che vengano utilizzate le credenziali di amministratore.  
  
#### <a name="to-launch-from-a-browser-window"></a>Per l'avvio da una finestra del browser  
  
1.  Aprire un browser e passare alla directory `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
2.  Fare doppio clic su `dwconfig.exe` e quindi fare clic su **Esegui come amministratore**.  
  
#### <a name="to-launch-from-a-command-prompt"></a>Per l'avvio da un prompt dei comandi  
  
1.  Sul desktop, aprire il **avviare** menu, fare clic su **programmi**, fare clic su **Accessori**, fare doppio clic su **prompt dei comandi** e quindi fare clic su  **Esegui come amministratore**.  
  
2.  Al prompt dei comandi, immettere il comando seguente per passare alla directory: `cd /d "C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100"`.  
  
3.  Al prompt dei comandi, immettere `dwconfig.exe`.  
  
Dopo il **Configuration Manager** viene avviato, si noterà tutte le funzionalità disponibili elencate nel riquadro a sinistra. Nella parte restante di questa sezione viene illustrato come eseguire ogni operazione disponibile nello strumento.  
  
Per chiudere e uscire **Configuration Manager**, fare clic su **uscire** nell'angolo in basso a destra di qualsiasi schermata.  
  
![SQL_Server_PDW_DWConfig_ApplTop](./media/launch-the-configuration-manager/SQL_Server_PDW_DWConfig_ApplTop.png "SQL_Server_PDW_DWConfig_ApplTop")  
  
## <a name="see-also"></a>Vedere anche  
[Monitorare il dispositivo tramite la Console di amministrazione &#40; Sistema della piattaforma Analitica &#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
