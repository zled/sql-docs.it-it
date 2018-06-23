---
title: Eseguire una valutazione su richiesta utilizzando Esplora oggetti | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 55ca364c60c2b9fcca407561ed195035ce7205fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067096"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a>Esecuzione di una valutazione su richiesta utilizzando Esplora oggetti
  In questa attività verrà utilizzato Esplora oggetti per eseguire una valutazione su richiesta di criteri per procedure consigliate per il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] in una singola istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  È inoltre possibile valutare criteri in un'istanza singola mediante Server registrati. Per altre informazioni, vedere [eseguire una valutazione su richiesta utilizzando server registrati](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Questa lezione è basata sulla versione di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Per eseguire una valutazione su richiesta dei criteri consigliate in istanze che eseguono [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], è necessario utilizzare la procedura nell'argomento [eseguirà una valutazione su richiesta dal server registrati mediante](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a>Per eseguire una valutazione su richiesta utilizzando Esplora oggetti  
  
1.  Avviare [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], quindi connettersi al [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  In Esplora oggetti espandere **Management**, espandere **Gestione criteri**, fare doppio clic su **criteri**, quindi fare clic su **Evaluate**.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, l'istanza locale viene utilizzata come origine dei criteri. Se in precedenza sono stati importati criteri per procedure consigliate, questi verranno elencati insieme agli altri criteri creati. È possibile selezionare uno qualsiasi dei criteri consigliate importati e quindi fare clic su **Evaluate**. Se non sono stati importati criteri per procedure consigliate, continuare con questa procedura.  
  
3.  Nel **valuta criteri** accanto alla finestra di dialogo il **origine** fare clic sui puntini di sospensione (**...** ) pulsante.  
  
4.  Nel **Seleziona origine** della finestra di dialogo è possibile selezionare **file** o **Server** come origine dei file di criteri da valutare. Se si fa clic su **Server**, è possibile eseguire una valutazione su richiesta di eventuali criteri consigliate precedentemente importati nella gestione basata su criteri in un server locale o remoto. In questa esercitazione, potrà fare clic su **file**e quindi selezionare i file dei criteri individuali che si desidera valutare. A tale scopo, eseguire le operazioni seguenti:  
  
    1.  Fare clic su **file**.  
  
    2.  Accanto a **file**, fare clic sui puntini di sospensione (**...** ) pulsante.  
  
    3.  Nel **Seleziona criteri** finestra di dialogo, passare alla cartella seguente, che contiene il migliori criteri per procedure consigliate:  
  
         **C:\Programmi\Microsoft file (x86) \Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
        > [!NOTE]  
        >  Il percorso del file può variare in base alla posizione in cui sono stati installati i file di programma di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], all'esecuzione di un sistema operativo a 32 o a 64 bit e all'identificatore di lingua.  
  
    4.  Selezionare uno o più file con estensione XML dei criteri per valutare e quindi fare clic su **Open**.  
  
         Verrà visualizzato l'elenco di file selezionati nel **file** casella.  
  
    5.  Nel **Seleziona origine** finestra di dialogo, fare clic su **OK**.  
  
    6.  Se il **caricamento criteri** verrà visualizzata la finestra di dialogo, fare clic su **Chiudi**.  
  
     I criteri selezionati vengono elencati nella **selezione criteri** pagina. L'icona di avviso accanto ai criteri indica che questi contengono script.  
  
5.  Fare clic su **Evaluate** per valutare i criteri.  
  
     Nel **risultati** di tabella, i risultati per tutti i criteri sono elencati. Un'icona "x" rossa indica che la conformità di criteri non è riuscita.  
  
6.  Per alcuni errori relativi ai criteri, la gestione basata su criteri consente di applicare immediatamente la conformità di criteri nella destinazione. Per questo tipo di errori verrà visualizzata una casella di controllo accanto ai criteri che presentano errori. Se si seleziona la casella di controllo, il **applica** diventa disponibile. Quando fa clic su **applica**, l'impostazione non conforme verrà automaticamente aggiornata nell'istanza di destinazione.  
  
    > [!CAUTION]  
    >  Assicurarsi di aver compreso a pieno tutte le impostazioni dei criteri prima di aggiornare automaticamente un'istanza di destinazione. È consigliabile che dopo aver selezionato una o più caselle di controllo, si fa clic su **Script**, scegliere un percorso di output in modo che è possibile esaminare sottostante [!INCLUDE[tsql](../includes/tsql-md.md)] prima di applicare le modifiche del codice.  
  
7.  Per visualizzare i risultati dettagliati per un criterio, fare clic sul criterio nel **risultati** tabella.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Eseguire una valutazione su richiesta utilizzando server registrati](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  