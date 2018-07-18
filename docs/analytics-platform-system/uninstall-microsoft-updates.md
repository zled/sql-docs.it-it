---
title: Disinstallazione di aggiornamenti Microsoft - Analitica Platform System | Documenti di Microsoft"
description: Disinstallazione di aggiornamenti Microsoft nel sistema della piattaforma Analitica (AP).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 57d0eb3616cf3567f63d75029f79cea6709ed955
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538551"
---
# <a name="uninstall-microsoft-updates-in-analytics-platform-system"></a>Disinstallazione di aggiornamenti Microsoft nel sistema della piattaforma Analitica
In questo articolo viene descritto come disinstallare un aggiornamento di Microsoft installato in precedenza sull'accessorio Analitica Platform System.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
### <a name="prerequisites"></a>Prerequisiti  
Per eseguire queste operazioni, è necessario:  
  
-   Un account di accesso Analitica Platform System con autorizzazioni per accedere alla Console di amministrazione per il monitoraggio del dispositivo.  
  
-   Informazioni dell'account amministratore di dominio dell'infrastruttura per accedere ai  *<Fabric Domain>* * *-HST01** nodo.  
  
## <a name="HowToUninstallMSFT"></a>Per disinstallare gli aggiornamenti Microsoft  
  
1.  Accedi per il  *<Fabric Domain>* * *-HST01** nodo come amministratore di dominio dell'infrastruttura.  
  
2.  Per disinstallare tutti gli aggiornamenti approvati per Windows Server Update Services disinstallare, aprire una finestra del prompt dei comandi e immettere il comando seguente. Sostituire gli elementi di segnaposto *< >* con le informazioni appropriate.  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni, vedere:
- [Scaricare e applicare gli aggiornamenti di Microsoft &#40;Analitica Platform System&#41;](download-and-apply-microsoft-updates.md) 
- [Applicare aggiornamenti rapidi di sistema della piattaforma Analitica &#40;Analitica Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
- [Disinstallare Analitica piattaforma sistema hotfix &#40;Analitica Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
- [Manutenzione del software &#40;Analitica Platform System&#41;](software-servicing.md)  
  
