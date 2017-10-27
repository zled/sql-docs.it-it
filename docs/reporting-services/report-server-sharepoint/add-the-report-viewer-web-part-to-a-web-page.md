---
title: Aggiungere la web part Visualizzatore Report a una pagina web | Documenti Microsoft
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
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 26080938c9849d6021f30d970ab2262f405df00c
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="add-the-report-viewer-web-part-to-a-web-page"></a>Aggiungere la web part Visualizzatore Report a una pagina web

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

È possibile utilizzare la web part Visualizzatore Report per visualizzare i report eseguiti nel server di report configurato per l'esecuzione in SharePoint modalità integrata. È possibile utilizzare la web part per visualizzare i file di definizione (con estensione rdl) report creati in Generatore Report o progettazione Report e caricati in una raccolta.

Se si desidera incorporare un report nella pagina, è possibile aggiungere la web part Visualizzatore Report a una pagina web.

> [!NOTE]
> Questo articolo è specifico per la web part Visualizzatore Report forniti con il componente aggiuntivo di Reporting Services per prodotti SharePoint. Integrazione con SharePoint di Reporting Services non è più disponibile dopo SQL Server 2016.

Per aggiungere una web part a una pagina web, è necessario disporre dell'autorizzazione aggiunta e personalizzazione pagine a livello di sito. Se si usano impostazioni di sicurezza predefinite, questa autorizzazione è concessa ai membri del gruppo **Proprietari** che hanno il livello di autorizzazione Controllo completo.

## <a name="to-embed-a-report-in-a-web-page"></a>Per incorporare un report in una pagina web

1.  Aprire o creare la pagina web part o un dashboard.  
  
2.  Nella pagina **Azioni sito**fare clic su **Modifica pagina**.  
  
3.  Fare clic su **aggiungere una web part**.  
  
4.  Nell'elenco delle categorie di web part selezionare la categoria **Varie** e quindi selezionare **Visualizzatore report di SQL Server Reporting Services**.  
  
5.  Scegliere **Aggiungi**. La web part viene aggiunta nella parte superiore della zona. È possibile trascinarla in una posizione diversa all'interno dell'area.  
  
6.  Nel visualizzatore fare clic su **Fare clic qui per aprire il riquadro Strumenti**.  
  
7.  Fare clic sul pulsante per la ricerca (**...**) e selezionare un report da una raccolta della raccolta siti corrente. In alternativa è possibile digitare l'URL del report. Per determinare l'URL di un report, fare clic con il pulsante destro del mouse sul report e scegliere **Proprietà**. Non fare clic sulla freccia verso il basso visualizzata accanto al report. L'URL del report non è indicato nella pagina Visualizza proprietà dell'elemento. Se si copia e si incolla l'URL dalla finestra di dialogo **Proprietà** , sostituire con uno spazio tutte le occorrenze del codice "%20" presenti nell'URL. Ad esempio, modificare "Vendite%20azienda" in "Vendite azienda".  
  
    > [!NOTE]  
    >  Ogni web part Visualizzatore Report contiene un singolo report. L'URL deve essere costituito dal percorso completo di un report presente nel sito di SharePoint corrente oppure in un sito disponibile nella stessa farm o applicazione Web. L'URL deve corrispondere a una raccolta documenti o a una cartella all'interno della raccolta documenti che contiene il report e deve includere l'estensione rdl del file. Se il report dipende da un file modello o di origine dati condivisa, non sarà necessario specificare tali file nell'URL, perché il report contiene riferimenti a tutti i file necessari.  
  
8.  Quando il riquadro Strumenti è aperto è possibile impostare alcune proprietà per modificare il layout e l'aspetto predefiniti.  
  
9. Fare clic sul pulsante **Applica** , disponibile nella parte inferiore del riquadro Strumenti, e quindi scegliere **OK** per chiudere il riquadro.  
  
## <a name="see-also"></a>Vedere anche

 [Web part Visualizzatore di report in un sito di SharePoint](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
 [Personalizzare la web part Visualizzatore Report](../../reporting-services/report-server-sharepoint/customize-the-report-viewer-web-part.md)   
 [Concessione di autorizzazioni per elementi del server di report in un sito di SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Installare o disinstallare il componente aggiuntivo Reporting Services per SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  

