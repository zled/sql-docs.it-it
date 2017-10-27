---
title: La connessione web part di filtro o documenti con una web part Visualizzatore Report di Reporting Services | Documenti Microsoft
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 87d4b4a3f0c01804329f3a7b0688632c20ed6c9b
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="connect-filter-or-documents-web-part-with-a-reporting-services-report-viewer-web-part"></a>La connessione web part di filtro o documenti con una web part Visualizzatore Report di Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Se si utilizza un prodotto SharePoint, è possibile creare un dashboard o web parte pagina che include una web part filtro o web part documenti e una web part Visualizzatore Report. Le versioni supportate sono [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] o [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]. Sono anche supportate le versioni [!INCLUDE[winSPServ3](../../includes/winspserv3-md.md)] e [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007. Tramite la connessione web part di filtro, gli utenti che selezionano valori di filtro in una web part di filtro è possono inviare il valore a un report con parametri nella stessa pagina. Connettendosi a una web part documenti, utenti, fare clic su report nella raccolta documenti è possono visualizzare il report in una web part di Visualizzatore Report adiacente.

> [!NOTE]
> Integrazione con SharePoint di Reporting Services non è più disponibile dopo SQL Server 2016.

 La web part di filtro viene utilizzata per inviare i valori per uno o più parametri in un report. Per utilizzare una web part di filtro, il report deve avere parametri definiti per tale che siano compatibili con i valori, un tipo di dati e un formato inviati dalla web part.  
  
 La web part documenti è associata a una raccolta documenti del sito principale. Per visualizzare, aggiungere o rimuovere elementi dalla raccolta Documenti, fare clic su **Visualizza tutto il contenuto del sito**. In Raccolte fare clic su **Documenti**. Per gestire gli elementi della raccolta Documenti, è possibile usare i menu **Nuovo**, **Carica**e **Azioni** .  
  
## <a name="connect-a-filter-web-part"></a>Connettere una web part di filtro
  
1.  Aprire o creare la pagina web part o un dashboard.  
  
2.  Scegliere **Modifica pagina** dal menu **Azioni sito**.  
  
3.  Fare clic su **aggiungere una web part**.  
  
4.  In **tutte le web part**nella **varie** categoria, seleziona **Visualizzatore Report di SQL Server Reporting Services**.  
  
5.  Scegliere **Aggiungi**. La web part viene aggiunta nella parte superiore della zona.  
  
6.  In un'altra area nella stessa pagina web part o dashboard, fare clic su **aggiungere una web part**.  
  
7.  In **tutte le web part**nella **filtri** , selezionare una web part.  
  
8.  Scegliere **Aggiungi**. La web part viene aggiunta nella parte superiore della zona.  
  
9. Nell'area che contiene la web part, selezionare la web part **modifica** dal menu **connessioni**, scegliere **Invia valori filtro a**, quindi selezionare **Report Visualizzatore** - *nome report*.  
  
10. Archiviare le modifiche e salvare la pagina.  
  
## <a name="connect-a-documents-web-part"></a>Connettere una web part documenti  
  
1.  Aprire o creare la pagina web part o un dashboard.  
  
2.  Scegliere **Modifica pagina** dal menu **Azioni sito**.  
  
3.  Fare clic su **aggiungere una web part**.  
  
4.  In **tutte le web part**nella **elenchi e raccolte** selezionare **documenti.**  
  
5.  Scegliere **Aggiungi**. La web part viene aggiunta nella parte superiore della zona.  
  
6.  Fare clic sul pulsante **Applica** , disponibile nella parte inferiore del riquadro Strumenti, e quindi scegliere **OK** per chiudere il riquadro.  
  
7.  In un'altra area nella stessa pagina web part o dashboard, fare clic su **aggiungere una web part**.  
  
8.  In **tutte le web part**nella **varie** categoria, seleziona **Visualizzatore Report di SQL Server Reporting Services.**  
  
9. Scegliere **Aggiungi**. La web part viene aggiunta nella parte superiore della zona.  
  
10. Nell'area che contiene la web part, selezionare la web part **modifica** dal menu **connessioni**, scegliere **recupera definizioni report da**, quindi selezionare  **Documenti**.  
  
11. Archiviare le modifiche e salvare la pagina.  
  
## <a name="see-also"></a>Vedere anche

 [Aggiungere la web part Visualizzatore Report a una pagina web](../../reporting-services/report-server-sharepoint/add-the-report-viewer-web-part-to-a-web-page.md)   
 [Web part Visualizzatore di report in un sito di SharePoint](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
 [Personalizzare la web part di Visualizzatore di report](../../reporting-services/report-server-sharepoint/customize-the-report-viewer-web-part.md)  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

