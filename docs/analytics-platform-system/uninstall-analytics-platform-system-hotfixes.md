---
title: Disinstallare Analitica piattaforma sistema correzioni (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c9ab596d-3f5a-48e2-bce7-c9be99b8c23b
caps.latest.revision: "21"
ms.openlocfilehash: 32d733f2e05855eb361095d23d6c34acefd343dc
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Disinstallare gli aggiornamenti rapidi del sistema di piattaforma Analitica
I passaggi seguenti viene descritto come disinstallare un hotfix Analitica Platform System installato in precedenza.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
### <a name="prerequisites"></a>Prerequisites  
Per eseguire queste operazioni, è necessario:  
  
-   Un account di accesso Analitica Platform System con autorizzazioni per accedere alla Console di amministrazione per il monitoraggio del dispositivo.  
  
-   L'account amministratore di dominio di accesso per il *< appliance_domain >***-HST01** nodo.  
  
-   La Knowledge base di per l'aggiornamento rapido per disinstallare.  
  
## <a name="HowToUninstallPDW"></a>Per disinstallare un hotfix di SQL Server PDW  
  
1.  Eseguire l'accesso di *< appliance_domain >***-HST01** nodo come amministratore di dominio dell'infrastruttura.  
  
2.  Utilizzare l'esecuzione come opzione di amministratore per aprire un prompt dei comandi.  
  
3.  Passare alla directory `C:\PDWINST\Patches\<kbarticle>\media` in  *<kbarticle>*  è il numero di articolo della Knowledge Base per l'aggiornamento rapido da disinstallare.  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  Per rimuovere l'aggiornamento rapido, eseguire il comando seguente.  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>Vedere anche  
[Scaricare e applicare gli aggiornamenti di Microsoft &#40; Sistema della piattaforma Analitica &#41;](download-and-apply-microsoft-updates.md)  
[Disinstallare gli aggiornamenti di Microsoft &#40; Sistema della piattaforma Analitica &#41;](uninstall-microsoft-updates.md)  
[Applica gli hotfix del sistema di piattaforma Analitica &#40; Sistema della piattaforma Analitica &#41;](apply-analytics-platform-system-hotfixes.md)  
[Software di manutenzione &#40; Sistema della piattaforma Analitica &#41;](software-servicing.md)  
  
