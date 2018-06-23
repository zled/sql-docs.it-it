---
title: Apertura di progetti dal controllo del codice sorgente | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [SQL Server Management Studio], opening
- opening projects
ms.assetid: 942f93a3-e264-4ec4-ba72-a28e0509a527
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0963ef46d2378cd23eae5c1cec23b76c0919e3d1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168577"
---
# <a name="open-projects-from-source-control"></a>Apertura di progetti dal controllo del codice sorgente
  È possibile utilizzare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per aprire i progetti direttamente dal controllo del codice sorgente. Quando si esegue questa operazione, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] recupera la versione più recente del progetto e li copia nel disco locale. Nell'ambiente [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] viene inoltre creata automaticamente una soluzione per il progetto.  
  
 Dopo aver aperto un progetto dal controllo del codice sorgente, è possibile estrarre e modificare i file di progetto.  
  
> [!NOTE]  
>  Utilizzare la procedura seguente una sola volta. Successivamente, è necessario aprire il progetto come qualsiasi altro progetto (facendo clic **File**, **aprire**, quindi **progetto**).  
  
### <a name="to-open-a-project-from-source-control"></a>Per aprire un progetto dal controllo del codice sorgente  
  
1.  Nel **File** dal menu **controllo del codice sorgente**, fare clic su **Apri dal controllo del codice sorgente**.  
  
2.  Se richiesto, accedere a [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.  
  
3.  Nel **Crea progetto locale da SourceSafe** dialogo casella, aprire la cartella che contiene il progetto da aprire.  
  
4.  Il **creare un nuovo progetto nella cartella** finestra modifiche per identificare la directory locale in cui verrà creato il progetto. Se si desidera inserire il progetto in una directory diversa, digitare il percorso nella directory o utilizzare il **Sfoglia** pulsante per individuare la directory sul disco locale.  
  
5.  Nel **creare un nuovo progetto nella cartella**, verificare che viene visualizzato nella cartella corretta e quindi fare clic su **OK**.  
  
6.  Nel **Apri soluzione** finestra di dialogo, selezionare il progetto da aprire e fare clic su **aprire**.  
  
## <a name="see-also"></a>Vedere anche  
 [Aprire soluzioni e progetti dal controllo del codice sorgente](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)   
 [Aprire Soluzioni dal controllo del codice sorgente](../../2014/database-engine/open-solutions-from-source-control.md)  
  
  