---
title: Installazione degli aggiornamenti dal prompt dei comandi | Microsoft Docs
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: install-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc98ba2b-aae9-4d01-aa85-d4c36428cb0b
caps.latest.revision: 18
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 96288325de3f2e7783a43fc1b14197b98c6f89ef
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="installing-updates-from-the-command-prompt"></a>Installazione degli aggiornamenti dal prompt dei comandi

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Provare gli script di installazione e adattarli alle esigenze della propria azienda. 
 
## <a name="sample-syntax-for-installation"></a>Sintassi di esempio per l'installazione 
Il nome del pacchetto di aggiornamento può variare e includere una lingua, un'edizione e un componente processore. Applicare un aggiornamento dal prompt dei comandi sostituendo <package_name> con il nome del pacchetto di aggiornamento. 
 
- Aggiornare una sola istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e tutti i componenti condivisi, quali [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e gli strumenti di gestione. È possibile specificare l'istanza tramite il parametro InstanceName o il parametro InstanceID. Per aggiornare un'istanza predisposta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario specificare il parametro InstanceID.

    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance
    ```
    o Gestione configurazione 
    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceID=\<Instance ID>. 
    ```

- La configurazione consente di integrare gli aggiornamenti più recenti del pacchetto con l'installazione del prodotto principale, in modo che il prodotto principale e i relativi aggiornamenti applicabili vengano installati contemporaneamente. È possibile preparare un'installazione dell'istanza del motore di database affinché includa l'aggiornamento del prodotto: 

    ```
    setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=PrepareImage /UpdateEnabled=True /UpdateSource=\<path where the update is downloaded> /INSTANCEID=\<Instance ID> /FEATURES=SQLEngine. 
    ```

- Aggiornare solo i componenti condivisi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], come ad esempio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e gli strumenti di gestione: 

    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch 
    ```

- Aggiornare tutte le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel computer e tutti i componenti condivisi, come ad esempio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e gli strumenti di gestione: 

    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances. 
    ```

- Rimuovere un aggiornamento da una singola istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e tutti i componenti condivisi, come ad esempio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e gli strumenti di gestione: 

    ```
    <package_name>.exe /qs /Action=RemovePatch /InstanceName=MyInstance. 
    ```

- Eliminare un aggiornamento dai componenti condivisi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], come ad esempio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e gli strumenti di gestione: 

    ```
    <package_name>.exe /qs /Action=RemovePatch 
    ```

  > [!NOTE] 
  > Il programma di installazione dell'aggiornamento verifica che la versione dei componenti condivisi sia sempre corrispondente o superiore alla versione dell'istanza di livello più alto. 
 
## <a name="supported-parameters"></a>Parametri supportati 
 
> [!IMPORTANT] 
> Se possibile, specificare le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file di script, proteggere tale file per impedire l'accesso non autorizzato. 
 
|Opzione|Description| 
|------------|-----------------| 
|**/?**|Visualizza la Guida del prompt dei comandi per l'installazione automatica| 
|**/action=Patch or /action=RemovePatch**|Specifica l'azione di installazione: Patch o RemovePatch.| 
|**/allinstances**|Applica l'aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a tutte le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e a tutti i componenti condivisi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che non supportano le istanze.| 
|**/instancename=InstanceName***|Applica l'aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] denominata InstanceName e a tutti i componenti condivisi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che non supportano le istanze.| 
|**/InstanceID=Inst1**|Applica l'aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all'istanza Inst1 di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e a tutti i componenti condivisi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che non supportano le istanze.| 
|**/quiet**|Esegue l'installazione dell'aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modalità automatica.| 
|**/qs**|Visualizza solo la finestra di dialogo dell'interfaccia utente relativa allo stato.| 
|**/UpdateEnabled**|Specifica se durante la configurazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] debbano essere individuati e inclusi aggiornamenti del prodotto. I valori validi sono True e False oppure 1 e 0. Per impostazione predefinita, gli aggiornamenti individuati verranno inclusi nel programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .| 
|**/IAcceptSQLServerLicenseTerms**|Obbligatorio solo quando il parametro /Q o /QS è specificato per le installazioni automatiche.| 
 
 *Non è possibile specificare questo parametro per applicare un aggiornamento a un'istanza predisposta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specificare il parametro /instanceID. 
 
## <a name="see-also"></a>Vedere anche 
 [Panoramica sull'installazione dei servizi SQL Server](http://msdn.microsoft.com/library/6a9fd19b-2367-4908-b638-363b1e929e1e) 
 
 
