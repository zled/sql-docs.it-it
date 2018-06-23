---
title: Impostare o modificare il metodo di connessione preferito per DirectQuery | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f10d5678-d678-4251-8cce-4e30cfe15751
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bf6abf3e4576fb28155529ee1bdfd24520176010
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168394"
---
# <a name="set-or-change-the-preferred-connection-method-for-directquery"></a>Impostare o modificare il metodo di connessione preferito per DirectQuery
  Quando si crea un modello per l'utilizzo nella modalità DirectQuery, è innanzitutto necessario configurare l'ambiente di progettazione affinché supporti l'utilizzo di DirectQuery. A tale scopo, vedere [abilitare la modalità DirectQuery &#40;modello tabulare di SSAS&#41;](tabular-models/enable-directquery-mode-in-ssdt.md).  
  
 Prima di distribuire il modello, è necessario impostare alcune proprietà aggiuntive per consentire agli utenti di accedere al modello utilizzando una delle modalità DirectQuery:  
  
-   È necessario indicare se le query eseguite sul modello devono utilizzare i dati memorizzati nella cache o nell'origine dati relazionale. È possibile utilizzare una modalità ibrida o la modalità Solo DirectQuery.  
  
-   Se si utilizzano le partizioni, è necessario indicare quale utilizzare come origine dati DirectQuery.  
  
-   È necessario impostare le opzioni di rappresentazione per gli utenti che accederanno all'origine dati SQL Server.  
  
 In questa procedura viene illustrato come impostare il metodo di connessione preferito per un modello DirectQuery nella finestra di progettazione. Viene inoltre illustrato come modificare questa proprietà in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] dopo la distribuzione del modello.  
  
### <a name="to-set-the-preferred-connection-method-for-a-directquery-model"></a>Per impostare il metodo di connessione preferito per un modello DirectQuery  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], aprire il file della soluzione per il modello DirectQuery.  
  
2.  In Visual Studio scegliere **Proprietà** dal menu **Progetto**.  
  
3.  Nel riquadro **Proprietà** modificare la proprietà **DirectQueryMode**su uno dei valori che supportano l'utilizzo di DirectQuery:  
  
    -   **InMemorywithDirectQuery**: se si utilizza questa opzione, il modello viene distribuito, ma è necessario elaborare la cache prima di poter eseguire query sul modello.  
  
    -   **DirectQuery with InMemory**: se si utilizza questa opzione, la cache potrà essere utilizzata dai client se è già stata elaborata. Se si distribuisce il modello con questa impostazione e non si elabora la cache, alcuni client riceveranno un errore al tentativo di connettersi al modello.  
  
    -   **DirectQuery only:** se si utilizza questa opzione, i metadati vengono distribuiti, ma il modello non contiene dati. I client che tentano di connettersi utilizzando la modalità in memoria riceveranno un errore che indica che il modello non esiste o non è stato elaborato.  
  
4.  In caso di errori, in Visual Studio aprire l' **Elenco errori** e risolvere eventuali problemi che impedirebbero di distribuire il modello nella modalità DirectQuery.  
  
### <a name="to-verify-or-change-the-preferred-connection-method-for-a-directquery-model"></a>Per verificare o modificare il metodo di connessione preferito per un modello DirectQuery  
  
1.  In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] connettersi all'istanza in cui è stato distribuito il modello di DirectQuery.  
  
2.  Fare clic con il pulsante destro del mouse sul database modello, quindi scegliere **Proprietà**.  
  
3.  Nel riquadro **Proprietà** modificare la proprietà **DirectQueryMode**su uno di questi valori:  
  
    -   **Solo DirectQuery**  
  
    -   **In-Memory con DirectQuery**  
  
    -   **DirectQuery with InMemory**  
  
 Si noti che queste proprietà corrispondono alle proprietà impostate sul progetto prima della distribuzione in Visual Studio. È possibile modificare in qualsiasi momento la modalità di connessione preferita per la modalità DirectQuery, a condizione che il modello sia stato configurato per supportare l'utilizzo di DirectQuery.  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità DirectQuery &#40;SSAS tabulare&#41;](tabular-models/directquery-mode-ssas-tabular.md)   
 [Abilitare la modalità di progettazione DirectQuery &#40;tabulare di SSAS&#41;](tabular-models/enable-directquery-mode-in-ssdt.md)  
  
  