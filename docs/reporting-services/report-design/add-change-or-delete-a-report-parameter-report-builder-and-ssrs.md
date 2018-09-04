---
title: Aggiungere, modificare o eliminare un parametro di report (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d44a8e0a-10cf-4502-9391-09743ffc9bad
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9c6751843d730f01f609b19069bda900a4e9aebe
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2018
ms.locfileid: "40409512"
---
# <a name="add-change-or-delete-a-report-parameter-report-builder-and-ssrs"></a>Aggiungere, modificare o eliminare un parametro di report (Generatore report e SSRS)
  Un parametro di report consente di scegliere i dati del report, connettere report correlati e variare la presentazione del report. È possibile specificare un valore predefinito e un elenco di valori disponibili per consentire all'utente di modificare la selezione.  
  
 Dopo aver pubblicato un report, è possibile modificare i valori predefiniti, i valori disponibili e altre proprietà relative a un parametro di report sul server di report. Per fornire più set di valori predefiniti del parametro, è possibile creare report collegati. Per ulteriori informazioni, vedere la pagina relativa al [Parametri report &#40;Generatore report e Progettazione report&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
 Questo articolo descrive l'aggiunta di parametri di report a un report impaginato in [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] o in Progettazione report in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. È possibile aggiungere parametri di report anche a report per dispositivi mobili in [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]. Per ulteriori informazioni, vedere [Create mobile reports with SQL Server Mobile Report Publisher](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md) .  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-or-edit-a-report-parameter"></a>Per aggiungere o modificare un parametro di report  
  
1.  In [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] o in Progettazione report in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nel riquadro **Dati report** fare clic con il pulsante destro del mouse sul nodo **Parametri** e scegliere **Aggiungi parametro**. Verrà visualizzata la finestra di dialogo **Proprietà parametri report** .  
  
2.  In **Nome**digitare il nome del parametro o accettare il nome predefinito.  
  
3.  Nella casella **Messaggio di richiesta**digitare il testo da visualizzare accanto alla casella di testo del parametro quando l'utente esegue il report.  
  
4.  Nella casella **Tipo di dati**selezionare il tipo di dati per il valore del parametro.  
  
5.  Se il parametro può contenere un valore vuoto, selezionare **Consenti nessun valore**.  
  
6.  Se il parametro può contenere un valore Null, selezionare **Consenti valore Null**.  
  
7.  Per consentire agli utenti la selezione di più valori per il parametro, selezionare **Consenti più valori**.  
  
8.  Impostare l'opzione di visibilità.  
  
    -   Per visualizzare il parametro sulla barra degli strumenti all'inizio del report, selezionare **Visibile**.  
  
    -   Per nascondere il parametro in modo da non visualizzarlo sulla barra degli strumenti, selezionare **Nascosto**.  
  
    -   Per nascondere il parametro e proteggerlo da eventuali modifiche sul server di report in seguito alla relativa pubblicazione, selezionare **Interno**. Il parametro di report potrà essere visualizzato solo nella relativa definizione. Per questa opzione è necessario impostare un valore predefinito o consentire l'immissione di un valore Null per il parametro.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-report-parameter"></a>Per eliminare un parametro di report  
  
1.  Nel riquadro **Dati report** espandere il nodo **Parametri** .  
  
2.  Fare clic con il pulsante destro del mouse sul parametro di report, quindi scegliere **Elimina**.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere, modificare o eliminare valori disponibili per un parametro di report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-change-or-delete-available-values-for-a-report-parameter.md)   
 [Aggiungere, modificare o eliminare valori predefiniti per un parametro di report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-change-or-delete-default-values-for-a-report-parameter.md)   
 [Modificare l'ordine di un parametro del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)   
 [Parametri report &#40;Generatore report e Progettazione report&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Aggiunta di parametri di propagazione a un report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Esercitazione: Aggiungere un parametro al report &#40;Generatore report&#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Aggiungere filtri per set di dati, aree dati e gruppi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Riferimenti alla raccolta dei parametri &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)   
 [Aggiungere un parametro multivalore a un report](../../reporting-services/report-design/add-a-multi-value-parameter-to-a-report.md)  
  
  
