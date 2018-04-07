---
title: Disinstallare Analitica piattaforma sistema correzioni (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c9ab596d-3f5a-48e2-bce7-c9be99b8c23b
caps.latest.revision: 21
ms.openlocfilehash: 56c6731d5a39741574999d94532b9505adaf6380
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Disinstallare gli aggiornamenti rapidi del sistema di piattaforma Analitica
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
  
