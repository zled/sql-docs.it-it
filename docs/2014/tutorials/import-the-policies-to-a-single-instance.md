---
title: Importare i criteri in una singola istanza | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 945cd03bb574bc180af5567888a6d171966bccf6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157853"
---
# <a name="import-the-policies-to-a-single-instance"></a>Importazione dei criteri in un'istanza singola
  In questa attività verrà eseguita l'importazione dei criteri per procedure consigliate che si desidera pianificare nella gestione basata su criteri in una singola istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="prerequisites"></a>Prerequisiti  
 È necessario eseguire questa procedura in un server che esegue [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] o una versione successiva.  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a>Importazione dei criteri per procedure consigliate per il Motore di database  
  
1.  Avviare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], quindi connettersi al [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  In Esplora oggetti, espandere **Management**, quindi espandere **gestione dei criteri**.  
  
3.  Fare doppio clic su **criteri**, quindi fare clic su **Importa criteri**.  
  
4.  Nel **importare** accanto alla finestra di dialogo il **i file da importare** fare clic sui puntini di sospensione (**...** ) pulsante.  
  
5.  Nel **Cerca in** elencare, passare alla cartella seguente, che contiene il migliori criteri per procedure consigliate:  
  
     **C:\Programmi\Microsoft file (x86) \Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
    > [!NOTE]  
    >  Il percorso del file può variare in base alla posizione in cui sono stati installati i file di programma di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], all'esecuzione di un sistema operativo a 32 o a 64 bit e all'identificatore di lingua.  
  
6.  Nel **Seleziona criteri** finestra di dialogo, selezionare uno o più criteri file.  
  
     Per selezionare file non adiacenti, fare clic su un file, tenere premuto il tasto CTRL, quindi fare clic su ogni file aggiuntivo. Per selezionare file adiacenti, fare clic sul primo file nella sequenza, tenere premuto il tasto MAIUSC, quindi fare clic sull'ultimo file.  
  
7.  Dopo aver selezionato i file, fare clic su **Open**.  
  
8.  Nel **importare** finestra di dialogo casella, assicurarsi che il **lo stato dei criteri** elenco è impostato su **mantenere lo stato dei criteri durante l'importazione** (impostazione predefinita) e quindi fare clic su **OK**.  
  
     I criteri vengono importati il **criteri** nodo sotto **Gestione criteri di**. Per impostazione predefinita, i criteri importati sono impostati sulla modalità di valutazione "Su richiesta".  
  
## <a name="next-steps"></a>Passaggi successivi  
 [Pianificazione criteri](../../2014/tutorials/schedule-the-policies.md)  
  
  