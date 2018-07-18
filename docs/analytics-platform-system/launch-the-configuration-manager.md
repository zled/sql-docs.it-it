---
title: Avvia Configuration Manager - sistema di piattaforma Analitica | Documenti Microsoft
description: Istruzioni per l'avvio dello strumento di Configuration Manager per l'applicazione di sistema della piattaforma Analitica.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d2e7a726386aa64d04f87f30cd22328900b1e5cd
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31544783"
---
# <a name="launch-the-configuration-manager-in-analytics-platform-system"></a>Avviare Gestione configurazione nel sistema della piattaforma Analitica
In questo argomento vengono fornite istruzioni per l'avvio di **Configuration Manager** per l'applicazione di sistema della piattaforma Analitica.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
### <a name="prerequisites"></a>Prerequisiti  
Il sistema di piattaforma Analitica**Configuration Manager** può essere eseguito solo dall'amministratore del dominio applicazione. Per eseguire questo strumento, è necessario specificare la password per l'amministratore del dominio applicazione. Per creare altri amministratori di punti di accesso, vedere [creare un amministratore di dominio punti di accesso &#40;punti di accesso&#41;](create-an-aps-domain-administrator-aps.md).  
  
## <a name="Accessing"></a>Avviare lo strumento Gestione configurazione  
Per eseguire Gestione configurazione, utilizzare Desktop remoto per connettersi al nodo di controllo PDW (***PDW_region *-CTL01**) nodo e accedere come * appliance_domain ***\Administrator**. Quando si avvia il **Configuration Manager** di programma, utilizzare il **Esegui come amministratore** opzione per verificare che vengano utilizzate le credenziali di amministratore.  
  
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
[Monitorare il dispositivo tramite la Console di amministrazione &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
