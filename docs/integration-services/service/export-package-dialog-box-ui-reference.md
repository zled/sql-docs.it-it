---
title: "Riferimento all&#39;interfaccia utente della finestra di dialogo Esporta pacchetto | Microsoft Docs"
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
  - "sql13.dts.dtsserver.exportpackage.f1"
helpviewer_keywords: 
  - "Esporta pacchetto - finestra di dialogo"
ms.assetid: 3742fe8a-ef57-444d-b2fb-cb25d16bae97
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Riferimento all&#39;interfaccia utente della finestra di dialogo Esporta pacchetto
  Usare la finestra di dialogo **Esporta pacchetto** disponibile in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per esportare un pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in un percorso diverso ed eventualmente modificare il livello di protezione del pacchetto.  
  
## Opzioni  
 **Posizione pacchetto**  
 Consente di selezionare il tipo di archiviazione in cui esportare il pacchetto. Sono disponibili le opzioni seguenti:  
  
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
 Digitare il percorso del pacchetto oppure fare clic sul pulsante Sfoglia (**…**) e individuare la cartella in cui archiviare il pacchetto.  
  
 **Livello di protezione**  
 Fare clic sul pulsante Sfoglia (**…**) e aggiornare il livello di protezione nella finestra di dialogo **Livello di protezione pacchetto**. Per altre informazioni, vedere [Finestra di dialogo Livello di protezione pacchetto e Livello di protezione del progetto](../../integration-services/packages/package-and-project-protection-level-dialog-box.md).  
  
## Vedere anche  
 [Salva copia del pacchetto](../Topic/Save%20Copy%20of%20Package.md)   
 [Riferimento all'interfaccia utente della finestra di dialogo Importa pacchetto](../../integration-services/service/import-package-dialog-box-ui-reference.md)   
 [Salvataggio di pacchetti](../../integration-services/save-packages.md)   
 [Importare ed esportare pacchetti &#40;servizio SSIS&#41;](../../integration-services/service/import-and-export-packages-ssis-service.md)  
  
  