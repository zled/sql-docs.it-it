---
title: Riferimento all'interfaccia utente della finestra dialogo pacchetto di importazione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.importpackage.f1
helpviewer_keywords:
- Import Package dialog box
ms.assetid: 0e5fb127-c7ff-4dfa-b90e-d9bcf0ce763b
caps.latest.revision: 18
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e34f7c697df4b7c9ba183adfdf71753e47bf6619
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245561"
---
# <a name="import-package-dialog-box-ui-reference"></a>Riferimento all'interfaccia utente della finestra di dialogo Importa pacchetto
  Usare la finestra di dialogo **Importa pacchetto** disponibile in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per importare un pacchetto [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e impostare o modificare il livello di protezione del pacchetto.  
  
## <a name="options"></a>Opzioni  
 **Posizione pacchetto**  
 Selezionare il tipo di percorso di archiviazione da cui importare il pacchetto. Sono disponibili le opzioni seguenti:  
  
 **SQL Server**  
  
 **File system**  
  
 **Archivio pacchetti SSIS**  
  
 **Server**  
 Consente di digitare il nome del server o di selezionarlo nell'elenco.  
  
 **Autenticazione**  
 Consente di selezionare l'autenticazione di Windows o l'autenticazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Questa opzione è disponibile solo se è stato selezionato il percorso di archiviazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Se possibile, è consigliabile utilizzare l'autenticazione di Windows.  
  
 **Tipo di autenticazione**  
 Consente di selezionare un tipo di autenticazione.  
  
 **Nome utente**  
 Se si utilizza l'autenticazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , specificare un nome utente.  
  
 **Password**  
 Se si utilizza l'autenticazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , specificare una password.  
  
 **Percorso pacchetto**  
 Digitare il percorso del pacchetto oppure fare clic sul pulsante Sfoglia **(…)** per individuare il pacchetto.  
  
 **Nome pacchetto**  
 Se lo si desidera, rinominare il pacchetto. Il nome predefinito è il nome del pacchetto da importare.  
  
 **Livello di protezione**  
 Fare clic sul pulsante Sfoglia **(…)** e aggiornare il livello di protezione nella finestra di dialogo **Livello di protezione pacchetto** . Per altre informazioni, vedere [Finestra di dialogo Livello di protezione pacchetto e Livello di protezione del progetto](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Salva copia del pacchetto](../../2014/integration-services/save-copy-of-package.md)   
 [Riferimento all'interfaccia utente della finestra dialogo pacchetto di esportazione](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [Salvare i pacchetti](save-packages.md)   
 [Importare ed esportare pacchetti &#40;servizio SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
