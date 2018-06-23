---
title: Esportare riferimento all'interfaccia utente della finestra dialogo pacchetto | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.dtsserver.exportpackage.f1
helpviewer_keywords:
- Export Package dialog box
ms.assetid: 3742fe8a-ef57-444d-b2fb-cb25d16bae97
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ecbe181c790e1d839a0ccd6d7c96849a2e8512c5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166201"
---
# <a name="export-package-dialog-box-ui-reference"></a>Riferimento all'interfaccia utente della finestra di dialogo Esporta pacchetto
  Usare la finestra di dialogo **Esporta pacchetto** disponibile in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per esportare un pacchetto [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in un percorso diverso ed eventualmente modificare il livello di protezione del pacchetto.  
  
## <a name="options"></a>Opzioni  
 **Posizione pacchetto**  
 Consente di selezionare il tipo di archiviazione in cui esportare il pacchetto. Sono disponibili le opzioni seguenti:  
  
 **SQL Server**  
  
 **File System**  
  
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
 Digitare il percorso del pacchetto oppure fare clic sul pulsante Sfoglia ( **…** ) e individuare la cartella in cui archiviare il pacchetto.  
  
 **Livello di protezione**  
 Fare clic sul pulsante Sfoglia ( **…** ) e aggiornare il livello di protezione nella finestra di dialogo **Livello di protezione pacchetto** . Per altre informazioni, vedere [Finestra di dialogo Livello di protezione pacchetto e Livello di protezione del progetto](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Salva copia del pacchetto](../../2014/integration-services/save-copy-of-package.md)   
 [Riferimento all'interfaccia utente di finestra dialogo di importazione del pacchetto](../../2014/integration-services/import-package-dialog-box-ui-reference.md)   
 [Salvare i pacchetti](save-packages.md)   
 [Importare ed esportare pacchetti &#40;servizio SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  