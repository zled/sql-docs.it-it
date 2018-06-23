---
title: 'Attività 12: Individuazione delle informazioni (individuazione informazioni) | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dd80a8e6-1e41-4c49-9898-02b1d2505a10
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b608a384e5281134ae951fdfeca0e89234c4a32a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069513"
---
# <a name="task-12-discovering-knowledge-knowledge-discovery"></a>Attività 12: Individuazione delle informazioni (Individuazione informazioni)
  In questa attività si esegue il **individuazione informazioni** attività nei **Supplier ID** e **Supplier Name** domini. In questo scenario, tramite il processo di individuazione delle informazioni vengono importati principalmente i valori per questi due domini.  
  
 In questa esercitazione viene avviata la compilazione di una Knowledge Base nuova. Inoltre, è possibile avviare la creazione di una Knowledge Base eseguendo un'attività di individuazione delle informazioni. Quando fa clic su **creare una Knowledge Base** nella pagina principale, il client DQS consente di passare a una pagina con **gestione dei domini** attività selezionata per l'attività. È possibile modificare il **attività** alla **l'individuazione delle informazioni** e quindi nella pagina successiva è possibile creare domini come parte del processo di individuazione delle informazioni. Vedere [Perform Knowledge Discovery](http://msdn.microsoft.com/library/hh510398.aspx) per altri dettagli.  
  
1.  Nella pagina principale del Client DQS, nel **Knowledge Base recente** fare clic su **freccia destra** accanto al **Suppliers** knowledge base e fare clic su **Knowledge Base Individuazione**. In alternativa, è possibile fare clic su **Apri Knowledge Base**, selezionare **Suppliers** dal **elenco di knowledge base**, selezionare **l'individuazione delle informazioni**come **attività** e fare clic su **successiva**.  
  
     ![Menu individuazione informazioni nella Main pagina](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "Menu individuazione informazioni nella Main pagina")  
  
2.  Selezionare **il File di Excel** per **origine dati**.  
  
3.  Fare clic su **esplorare**, individuare e selezionare **Suppliers. xls**, fare clic su **aperta**.  
  
4.  Selezionare **Suppliers for Discovery** per **foglio di lavoro**.  
  
5.  Nel **mapping** sezione, eseguire il mapping **SupplierID** colonna dal **Excel** file per il **Supplier ID** dominio e  **Supplier Name** colonna per il **Supplier Name** dominio utilizzando **elenchi a discesa**. Il file di Excel contiene dati di esempio per la **Supplier ID** e **Supplier Name** domini. Durante il processo di individuazione, è possibile selezionare i domini di cui si desidera individuare i valori. È possibile creare i domini in questa pagina e, successivamente, eseguire il mapping delle colonne di origine ai domini in questione. In genere i domini vengono creati durante l'attività di individuazione delle informazioni e non durante l'attività di gestione dei domini.  
  
     ![Eseguire il mapping di pagina del processo di individuazione](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "eseguire il mapping di pagina del processo di individuazione")  
  
6.  Fare clic su **successivo** per attivare il **Discover** pagina.  
  
7.  Nel **Discover** fare clic su **avviare** per avviare il processo di individuazione. L'individuazione viene eseguita nelle colonne **SupplierID** e **Supplier Name** nel **Suppliers. xls** file. Il **Supplier ID** e **Supplier Name** domini devono essere popolati con le informazioni ricavate dall'individuazione.  
  
     ![Pagina del processo di individuazione individua](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "pagina del processo di individuazione individua")  
  
8.  Una volta completata l'analisi, esaminare i **statistiche origine** nel **scheda Profiler** nella parte inferiore della pagina. Si noti che 10 nuovi record con 20 valori totali (**SupplierID** e **Supplier Name** i valori di **foglio di lavoro di Excel**) sono stati individuati. Sarà possibile anche visualizzare quanti valori sono nuovi, univoci, nuovi e univoci, nonché validi. Nella casella di riepilogo a destra è possibile visualizzare ulteriori dettagli per ogni dominio coinvolto nel processo di individuazione. Se si posiziona il mouse sulla barra di stato nella colonna Completezza è possibile verificare l'eventuale mancanza di valori nelle colonne dell'origine.  
  
     ![Risultati dell'individuazione Knowledge](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "risultati dell'individuazione delle informazioni")  
  
9. Fare clic su **successivo** per attivare il **Gestisci valori di dominio** pagina.  
  
10. Nel **Gestisci valori di dominio** fare clic su **Supplier Name** dominio dall'elenco di domini.  
  
11. Nel riquadro destro, fare doppio clic su **Lazy Country Storex** (comunicazioni "x" alla fine) e selezionare **Lazy Country Store**. In DQS questa modifica viene suggerita dopo l'esecuzione del correttore ortografico nel dominio. Per impostazione predefinita, il correttore ortografico è abilitato nei domini creati.  
  
     ![Correzione nome fornitore - archivio paesi differito](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "correzione nome fornitore - archivio paesi differito")  
  
12. Nell'elenco di valori di dominio, verificare che il valore **Lazy Country Storex** viene impostato come un errore (rosso **X** contrassegnare) con **Lazy Country Store** come la correzione e anche il **Lazy Country Store** viene inoltre aggiunto come un valore valido.  
  
     ![Dominio valore e di correzione](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "dominio valore e di correzione")  
  
13. Fare clic su **Fine**.  
  
14. Nel **SQL Server Data Quality Services** finestra di dialogo, fare clic su **pubblica**.  
  
15. Fare clic su **OK** nella finestra di messaggio esito positivo.  
  
     È stata completata la prima lezione dell'esercitazione.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Lezione 2: Pulizia dei dati fornitore mediante la Knowledge Base Suppliers](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)  
  
  