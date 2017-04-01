---
title: "Riferimento all&#39;interfaccia utente della finestra di dialogo Ruoli pacchetto | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.dtsserver.packageroles.f1"
helpviewer_keywords: 
  - "Ruoli pacchetto - finestra di dialogo"
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Riferimento all&#39;interfaccia utente della finestra di dialogo Ruoli pacchetto
  Usare la finestra di dialogo **Ruoli pacchetto**, disponibile in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], per specificare i ruoli a livello di database che dispongono dell'accesso in lettura al pacchetto e quelli che dispongono dell'accesso in scrittura. I ruoli a livello di database si applicano solo ai pacchetti archiviati nel database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**.  
  
 Per altre informazioni sui ruoli a livello di database di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e le relative autorizzazioni, vedere [Ruoli Integration Services &#40;servizio SSIS&#41;](../../integration-services/service/integration-services-roles-ssis-service.md).  
  
 I ruoli elencati nella finestra di dialogo sono quelli attualmente disponibili nel database di sistema **msdb** . Se non viene selezionato alcun ruolo, viene applicato il ruolo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] predefinito. Per impostazione predefinita, il ruolo lettura include **db_ssisadmin**, **db_ssisoperator** e l'utente che ha creato il pacchetto. Gli utenti membri di uno di questi ruoli o creatori dei pacchetti possono enumerare, visualizzare, esportare ed eseguire i pacchetti. Per impostazione predefinita, il ruolo scrittura include **db_ssisadmin** e l'utente che ha creato il pacchetto. L'utente membro di questo ruolo e il creatore dei pacchetti possono importare, eliminare e modificare i pacchetti.  
  
 La colonna **ownersid** nella tabella **sysssispackages** include l'ID di sicurezza (SID) univoco dell'utente che ha creato il pacchetto.  
  
## Opzioni  
 **Nome pacchetto**  
 Consente di specificare il nome del pacchetto.  
  
 **Ruolo lettura**  
 Consente di selezionare un ruolo nell'elenco.  
  
 **Ruolo scrittura**  
 Consente di selezionare un ruolo nell'elenco.  
  
## Vedere anche  
 [Ruoli a livello di database](../../relational-databases/security/authentication-access/database-level-roles.md)   
 [Panoramica della sicurezza &#40;Integration Services&#41;](../../integration-services/security/security-overview-integration-services.md)  
  
  