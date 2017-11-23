---
title: Disinstallazione di aggiornamenti di Microsoft (Analitica piattaforma sistema)
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
ms.assetid: df61570a-210d-4154-822f-98acd721f075
caps.latest.revision: "19"
ms.openlocfilehash: c801918cbac5d0762384a0cd3adcca9ddf8f346a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="uninstall-microsoft-updates"></a>Disinstallazione di aggiornamenti Microsoft
In questo argomento viene descritto come disinstallare un aggiornamento di Microsoft installato in precedenza nel dispositivo di sistema della piattaforma Analitica.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
### <a name="prerequisites"></a>Prerequisiti  
Per eseguire queste operazioni, è necessario:  
  
-   Account di accesso di sistema della piattaforma Analitica con le autorizzazioni per accedere alla Console di amministrazione per il monitoraggio del dispositivo.  
  
-   Informazioni dell'account amministratore di dominio dell'infrastruttura di accesso per il  *<Fabric Domain>*  **-HST01** nodo.  
  
## <a name="HowToUninstallMSFT"></a>Per disinstallare gli aggiornamenti Microsoft  
  
1.  Account di accesso per il  *<Fabric Domain>*  **-HST01** nodo come amministratore di dominio dell'infrastruttura.  
  
2.  Per disinstallare tutti gli aggiornamenti approvati per Windows Server Update Services disinstallare, aprire una finestra del prompt dei comandi e immettere il comando seguente. Sostituire gli elementi di segnaposto *< >* con le informazioni appropriate.  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="see-also"></a>Vedere anche  
[Scaricare e applicare gli aggiornamenti di Microsoft &#40; Sistema della piattaforma Analitica &#41;](download-and-apply-microsoft-updates.md)  
[Applica gli hotfix del sistema di piattaforma Analitica &#40; Sistema della piattaforma Analitica &#41;](apply-analytics-platform-system-hotfixes.md)  
[Disinstallare gli aggiornamenti rapidi del sistema di piattaforma Analitica &#40; Sistema della piattaforma Analitica &#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Software di manutenzione &#40; Sistema della piattaforma Analitica &#41;](software-servicing.md)  
  
