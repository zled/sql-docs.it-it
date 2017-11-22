---
title: Applicare aggiornamenti rapidi del sistema di Analitica piattaforma (sistema di piattaforma Analitica)
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
ms.assetid: fca5eec9-86b8-4d20-b498-1678c367b5c8
caps.latest.revision: "25"
ms.openlocfilehash: af879486885f2c27ad4c3d80ef9a3d41279ff0ee
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="apply-analytics-platform-system-hotfixes"></a>Applicare aggiornamenti rapidi del sistema di piattaforma Analitica
In questo argomento viene descritto come applicare gli aggiornamenti rapidi per il software del sistema di piattaforma Analitica.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
> [!WARNING]  
> Non tentare di applicare un hotfix Analitica Platform System se all'applicazione o qualsiasi componente accessorio è inattivo o non riuscito su stato. In tal caso, contattare il supporto tecnico per assistenza.  
  
> [!WARNING]  
> Non applicare un hotfix Analitica piattaforma sistema mentre il dispositivo è in uso. L'applicazione di un hotfix potrebbe nodi dello strumento riavviare il computer. L'hotfix deve essere applicato in una finestra di manutenzione quando il dispositivo non è in uso.  
  
### <a name="prerequisites"></a>Prerequisiti  
Per eseguire queste operazioni, è necessario:  
  
-   Un accesso di sistema della piattaforma Analitica con le autorizzazioni per accedere alla Console di amministrazione per monitorare lo stato del dispositivo. <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   Informazioni dell'account amministratore di dominio dell'infrastruttura a cui connettersi il *< nome_dominio >***-HST01** nodo.  
  
## <a name="HowToInstallPDW"></a>Per applicare un hotfix Analitica Platform System  
A differenza degli aggiornamenti Microsoft, gli aggiornamenti rapidi per il software di sistema della piattaforma Analitica non vengono gestiti tramite WSUS. Si dispone di un flusso di lavoro diversi e vengono installati per l'esecuzione di un pacchetto di hotfix.  
  
1.  **Verificare gli indicatori di stato dello strumento.**  
  
    1.  Aprire la Console di amministrazione e passare alla pagina di stato dello strumento. Per ulteriori informazioni, vedere [monitorare il dispositivo tramite la Console di amministrazione &#40; Sistema della piattaforma Analitica &#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
    2.  Tutti gli indicatori rossi o gialli devono essere risolto prima di procedere al passaggio successivo. Due eccezioni sono:  
  
        -   Se sono presenti errori del disco, è possibile utilizzare la pagina degli avvisi di Console di amministrazione per verificare di non più di un errore di disco all'interno di ogni server o un array SAN. In caso di errore non più di un disco in ogni server o un array SAN, è possibile procedere al passaggio successivo prima di correggere errori del disco. Assicurarsi di contattare il supporto tecnico Microsoft per risolvere errori del disco appena possibile.  
  
        -   Se si verifica un errore di volume del disco (giallo) non critiche che non è presente nell'unità C:\, è possibile procedere al passaggio successivo prima di risolvere l'errore del volume del disco.  
  
2.  **Installare l'hotfix Analitica Platform System**  
  
    1.  Account di accesso per il <*appliance_domain*>-nodo HST01 come amministratore di dominio.  
  
    2.  Utilizzare il **Esegui come amministratore** opzione per aprire un prompt dei comandi.  
  
    3.  Eseguire il comando seguente, sostituendo  *<HotfixPackageName>*  con il nome del pacchetto eseguibile della correzione e sostituendo gli altri elementi di segnaposto *< >* con le informazioni appropriate.  
  
        ```  
        <HotfixPackageName> /DomainAdminPassword="<password>"  
        ```  
  
    4.  Seguire i passaggi presentato dal pacchetto hotfix.  
  
## <a name="see-also"></a>Vedere anche  
[Scaricare e applicare gli aggiornamenti di Microsoft &#40; Sistema della piattaforma Analitica &#41;](download-and-apply-microsoft-updates.md)  
[Disinstallare gli aggiornamenti di Microsoft &#40; Sistema della piattaforma Analitica &#41;](uninstall-microsoft-updates.md)  
[Disinstallare gli aggiornamenti rapidi del sistema di piattaforma Analitica &#40; Sistema della piattaforma Analitica &#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Software di manutenzione &#40; Sistema della piattaforma Analitica &#41;](software-servicing.md)  
  
