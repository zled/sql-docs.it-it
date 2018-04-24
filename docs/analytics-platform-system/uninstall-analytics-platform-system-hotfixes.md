---
title: Disinstallare gli aggiornamenti rapidi Analitica Platform System nel | Documenti Microsoft
description: Disinstallare gli aggiornamenti rapidi Analitica Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 83e57a676ee0eff21eb3a736484d8e286cdeee01
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Disinstallare gli aggiornamenti rapidi Analitica Platform System 
I passaggi seguenti viene descritto come disinstallare un hotfix Analitica Platform System installato in precedenza.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
### <a name="prerequisites"></a>Prerequisiti  
Per eseguire queste operazioni, è necessario:  
  
-   Un account di accesso Analitica Platform System con autorizzazioni per accedere alla Console di amministrazione per il monitoraggio del dispositivo.  
  
-   L'account amministratore di dominio eseguire l'accesso per il *< appliance_domain > * * *-HST01** nodo.  
  
-   La Knowledge base di per l'aggiornamento rapido per disinstallare.  
  
## <a name="HowToUninstallPDW"></a>Per disinstallare un hotfix di SQL Server PDW  
  
1.  Eseguire l'accesso di *< appliance_domain > * * *-HST01** nodo come amministratore di dominio dell'infrastruttura.  
  
2.  Utilizzare l'esecuzione come opzione di amministratore per aprire un prompt dei comandi.  
  
3.  Passare alla directory `C:\PDWINST\Patches\<kbarticle>\media` in *<kbarticle>* è il numero di articolo della Knowledge Base per l'aggiornamento rapido da disinstallare.  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  Per rimuovere l'aggiornamento rapido, eseguire il comando seguente.  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>Vedere anche  
[Scaricare e applicare gli aggiornamenti di Microsoft &#40;Analitica Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Disinstallazione di aggiornamenti Microsoft &#40;Analitica Platform System&#41;](uninstall-microsoft-updates.md)  
[Applicare aggiornamenti rapidi di sistema della piattaforma Analitica &#40;Analitica Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Manutenzione del software &#40;Analitica Platform System&#41;](software-servicing.md)  
  
