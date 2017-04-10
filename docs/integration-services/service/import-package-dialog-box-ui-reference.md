---
title: "Riferimento all&#39;interfaccia utente della finestra di dialogo Importa pacchetto | Microsoft Docs"
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
  - "sql13.dts.dtsserver.importpackage.f1"
helpviewer_keywords: 
  - "Importa pacchetto - finestra di dialogo"
ms.assetid: 0e5fb127-c7ff-4dfa-b90e-d9bcf0ce763b
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# Riferimento all&#39;interfaccia utente della finestra di dialogo Importa pacchetto
  Usare la finestra di dialogo **Importa pacchetto** disponibile in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per importare un pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e impostare o modificare il livello di protezione del pacchetto.  
  
## Opzioni  
 **Posizione pacchetto**  
 Selezionare il tipo di percorso di archiviazione da cui importare il pacchetto. Sono disponibili le opzioni seguenti:  
  
 **SQL Server**  
  
 **File system**  
  
 **Archivio pacchetti SSIS**  
  
 **Server**  
 Consente di digitare il nome del server o di selezionarlo nell'elenco.  
  
 **Autenticazione**  
 Consente di selezionare l'autenticazione di Windows o l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa opzione è disponibile solo se è stato selezionato il percorso di archiviazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Se possibile, è consigliabile utilizzare l'autenticazione di Windows.  
  
 **Tipo di autenticazione**  
 Consente di selezionare un tipo di autenticazione.  
  
 **Nome utente**  
 Se si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specificare un nome utente.  
  
 **Password**  
 Se si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specificare una password.  
  
 **Percorso pacchetto**  
 Digitare il percorso del pacchetto oppure fare clic sul pulsante Sfoglia **(…)** per individuare il pacchetto.  
  
 **Nome pacchetto**  
 Se lo si desidera, rinominare il pacchetto. Il nome predefinito è il nome del pacchetto da importare.  
  
 **Livello di protezione**  
 Fare clic sul pulsante Sfoglia **(…)** e aggiornare il livello di protezione nella finestra di dialogo **Livello di protezione pacchetto**. Per altre informazioni, vedere [Finestra di dialogo Livello di protezione pacchetto e Livello di protezione del progetto](../../integration-services/packages/package-and-project-protection-level-dialog-box.md).  
  
## Vedere anche  
 [Salva copia del pacchetto](../Topic/Save%20Copy%20of%20Package.md)   
 [Riferimento all'interfaccia utente della finestra di dialogo Esporta pacchetto](../../integration-services/service/export-package-dialog-box-ui-reference.md)   
 [Salvataggio di pacchetti](../../integration-services/save-packages.md)   
 [Importare ed esportare pacchetti &#40;servizio SSIS&#41;](../../integration-services/service/import-and-export-packages-ssis-service.md)  
  
  