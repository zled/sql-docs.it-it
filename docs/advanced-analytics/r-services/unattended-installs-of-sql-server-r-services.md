---
title: "Installazioni automatiche di SQL Server R Services | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: 18
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 14
---
# Installazioni automatiche di SQL Server R Services
    
Prima di iniziare il processo di installazione, tenere presenti questi requisiti:

+ È necessario installare il motore di database in ogni istanza in cui si utilizzerà servizi R (Database) in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
+ Se si esegue un'installazione offline, è necessario scaricare i componenti necessari di R in anticipo e copiarli in una cartella locale. Per i percorsi di download, vedere [installazione dei componenti di R senza accesso a Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).   
+ Esiste un nuovo parametro, */IACCEPTROPENLICENSETERMS*, che indica si hanno accettato le condizioni di licenza per utilizzare i componenti di R open source. Se non si include questo parametro nella riga di comando, il programma di installazione avrà esito negativo.  
  
## Eseguire un'istallazione automatica di R Services (In-Database)  
 L'esempio seguente illustra le funzionalità minime necessarie per specificare nella riga di comando quando si esegue un'installazione automatica e invisibile all'utente di servizi di R in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
###  <a name="bkmk_Unattended"></a>  
  
1.  Eseguire il comando seguente da un prompt dei comandi con privilegi elevati:  
  
    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,AdvancedAnalytics /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS  
    ```  
  
2.  Al termine dell'installazione, eseguire questo comando in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]per abilitare la funzionalità.  
  
    ```  
    Exec sp_configure  'external scripts enabled', 1  
    Reconfigure  with  override  
  
    ```  
  
    > [!NOTE]  
    >  È necessario abilitare esplicitamente la funzionalità del motore. In caso contrario, non sarà possibile richiamare gli script R anche se la funzionalità installata è stata configurata dal programma di installazione.  
  
3.  Riavviare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Viene riavviato automaticamente anche il servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] correlato.  
  
## Vedere anche  
 [Risoluzione dei problemi di installazione di R Services](../Topic/Troubleshooting%20R%20Services%20Setup.md)  
  
  