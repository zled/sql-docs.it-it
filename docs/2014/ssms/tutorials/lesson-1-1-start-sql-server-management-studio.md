---
title: Avviare SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
caps.latest.revision: 43
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2f928645fb89757b2284628d0400847cf5f3a1f2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055610"
---
# <a name="start-sql-server-management-studio"></a>Avviare SQL Server Management Studio
  Prima di iniziare questa esercitazione è opportuno esaminare brevemente [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="opening-sql-server-management-studio"></a>Apertura di SQL Server Management Studio  
  
#### <a name="to-open-sql-server-management-studio"></a>Per aprire SQL Server Management Studio  
  
1.  Nel **avviare** dal menu **tutti i programmi**, scegliere [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], quindi fare clic su **SQL Server Management Studio**.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] non è installato per impostazione predefinita. Se [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] non è disponibile, installarlo eseguendo il programma di installazione. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] non è disponibile con [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express è disponibile come download gratuito dal [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=37075&clcid=0x409), ma ha un'interfaccia utente diversa da quella descritta in questa esercitazione.  
  
2.  Nella finestra di dialogo **Connetti al server** verificare le impostazioni predefinite e quindi fare clic su **Connetti**. Per la connessione, il **nome del Server** casella deve contenere il nome del computer in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è installato. Se il [!INCLUDE[ssDE](../../includes/ssde-md.md)] è un'istanza denominata, il **nome del Server** finestra deve inoltre contenere il nome dell'istanza nel formato \< *nome_computer* > \\ < *nome_istanza*>.  
  
## <a name="management-studio-components"></a>Componenti di Management Studio  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] offre informazioni in finestre dedicate a tipi di informazioni specifiche. Le informazioni di database vengono visualizzate in Esplora oggetti e nelle finestre dei documenti.  
  
-   In Esplora oggetti è visualizzato l'albero di tutti gli oggetti di database presenti in un server. Possono essere inclusi i database del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]e di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Esplora oggetti contiene informazioni su tutti i server ai quali è connesso. All'apertura di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]viene chiesto di connettere Esplora oggetti alle ultime impostazioni utilizzate. È possibile fare doppio clic su un qualsiasi server nel componente Server registrati per eseguire la connessione, tuttavia non è necessario registrare un server per connettersi.  
  
-   La finestra del documento rappresenta la parte più estesa di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Le finestre dei documenti possono contenere editor di query e finestre del browser. Per impostazione predefinita, viene visualizzata la pagina Riepilogo connessa all'istanza di [!INCLUDE[ssDE](../../includes/ssde-md.md)] nel computer corrente.  
  
## <a name="showing-additional-windows"></a>Visualizzazione di finestre aggiuntive  
  
#### <a name="to-show-the-registered-servers-window"></a>Per visualizzare la finestra Server registrati  
  
1.  Scegliere **Server registrati** dal menu **Visualizza**.  
  
     La finestra Server registrati verrà visualizzata sopra Esplora oggetti. In Server registrati sono elencati i server gestiti più di frequente. È possibile aggiungere e rimuovere server dall'elenco. Gli unici server elencati saranno le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel computer in cui si esegue [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Se il server non viene visualizzato, nella finestra Server registrati, fare doppio clic su **motore di Database**, quindi fare clic su **Aggiorna registrazione Server locale**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Connettersi con Server registrati ed Esplora oggetti](../object/object-explorer.md)  
  
  