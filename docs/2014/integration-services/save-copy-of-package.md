---
title: Salva copia del pacchetto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.savecopyas.f1
helpviewer_keywords:
- Save Copy of Package dialog box
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0cd386cad85726707f1ce3ea9f7931bda4e66c25
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140501"
---
# <a name="save-copy-of-package"></a>Salva copia del pacchetto
  Usare la finestra di dialogo **Salva copia del pacchetto**, disponibile in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], per salvare una copia di un pacchetto [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] da [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] in un percorso diverso ed eventualmente modificarne il livello di protezione.  
  
## <a name="options"></a>Opzioni  
 **Posizione pacchetto**  
 Consente di selezionare il tipo di percorso di archiviazione in cui salvare la copia del pacchetto. Sono disponibili le opzioni seguenti:  
  
 **SQL Server**  
  
 **File system**  
  
 **Archivio pacchetti SSIS**  
  
 **Server**  
 Consente di digitare il nome del server o di selezionarlo nell'elenco. Questa opzione è disponibile solo se il percorso di archiviazione è **SQL Server** o **Archivio pacchetti SSIS**.  
  
 **Autenticazione**  
 Consente di selezionare l'autenticazione di Windows o l'autenticazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Questa opzione è disponibile solo se è stato selezionato il percorso di archiviazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Se possibile, utilizzare l'autenticazione di Windows.  
  
 **Tipo di autenticazione**  
 Consente di selezionare un tipo di autenticazione.  
  
 **Nome utente**  
 Se si utilizza l'autenticazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , specificare un nome utente.  
  
 **Password**  
 Se si utilizza l'autenticazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , specificare una password.  
  
 **Percorso pacchetto**  
 Consente di digitare il percorso del pacchetto. È inoltre possibile fare clic sul pulsante Sfoglia **(…)** per individuare la cartella in cui archiviare il pacchetto.  
  
 **Livello di protezione**  
 Fare clic sul pulsante Sfoglia **(…)** e aggiornare il livello di protezione nella finestra di dialogo **Livello di protezione pacchetto** . Per altre informazioni, vedere [Finestra di dialogo Livello di protezione pacchetto e Livello di protezione del progetto](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'interfaccia utente di finestra dialogo di importazione del pacchetto](../../2014/integration-services/import-package-dialog-box-ui-reference.md)   
 [Riferimento all'interfaccia utente della finestra dialogo pacchetto di esportazione](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [Salvare i pacchetti](save-packages.md)   
 [Importare ed esportare pacchetti &#40;servizio SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
