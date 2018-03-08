---
title: "Finestra di dialogo Proprietà set di dati, Query (Generatore report) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-data
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- "10024"
- sql13.rtp.rptdesigner.datasetproperties.query.f1
- "10160"
ms.assetid: 75432318-0b00-4797-917c-0a2e74f9d951
caps.latest.revision: "12"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f733d1c6013bb6f8110a52007e1a3cfa682bfecd
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="dataset-properties-dialog-box-query-report-builder"></a>Finestra di dialogo Proprietà set di dati, Query (Generatore report)
  Selezionare **Query** nella finestra di dialogo **Proprietà set di dati** per scegliere un set di dati condiviso da un server di report o per creare un set di dati incorporato. Per un set di dati incorporato, è necessario scegliere un'origine dati e compilare una query.  
  
 Nella finestra di dialogo **Proprietà set di dati** sono presenti le seguenti opzioni:  
  
-   [Finestra di dialogo Proprietà set di dati, Parametri &#40;Generatore report&#41;](http://msdn.microsoft.com/library/3a0672ad-c969-455b-b952-585164ce1dda)  
  
-   [Finestra di dialogo Proprietà set di dati, Campi &#40;Generatore report&#41;](http://msdn.microsoft.com/library/75c7e54a-3d20-4c9a-88da-ab36dce2ce42)  
  
-   [Finestra di dialogo Proprietà set di dati, Opzioni &#40;Generatore report&#41;](../../reporting-services/report-data/dataset-properties-dialog-box-options-report-builder.md)  
  
-   [Finestra di dialogo Proprietà set di dati, Filtri &#40;Generatore report&#41;](http://msdn.microsoft.com/library/933a6f44-4eb7-4e73-9c40-ac0fd17b23d3)  
  
 Per altre informazioni, vedere [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Consente di digitare un nome per il set di dati. Non è possibile specificare un nome uguale a quello di un'area dati o di un gruppo nel report.  
  
 **Usa un set di dati condiviso**  
 Selezionare questa opzione per utilizzare un set di dati predefinito dal server di report.  
  
 **Sfoglia**  
 Selezionare una cartella in un server di report o sito di SharePoint e scegliere un set di dati condiviso (estensione rsd).  
  
 **Usa un set di dati incorporato nel report**  
 Selezionare questa opzione per creare un set di dati da utilizzare solo per il report specifico.  
  
 **Data Source**  
 Consente di selezionare l'origine dati su cui basare il set di dati. Per creare una nuova origine dati, fare clic su **Nuova**.  
  
 **Tipo di query**  
 Consente di selezionare il tipo di comando o query da utilizzare per il set di dati. Selezionare **Testo** per eseguire una query che consenta di recuperare dati dal database. Selezionare **Tabella** per usare la funzionalità **TableDirect** di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e selezionare tutti i campi all'interno di una tabella. Selezionare **Stored procedure** per eseguire una stored procedure in base al nome. **Testo** è selezionato per impostazione predefinita e viene usato per la maggior parte delle query. Per modificare la query sull'origine dati selezionata, fare clic su **Progettazione query**.  
  
> [!NOTE]  
>  Non tutti i tipi di query sono supportati da tutte le origini dati. Il tipo **Tabella** , ad esempio, è supportato solo dalle origini dati di tipo **OLE DB** e **ODBC**.  
  
 **Query**  
 Questa opzione viene visualizzata quando si sceglie l'opzione del tipo di comando **Testo** . Digitare una query o importare una query preesistente facendo clic su **Importa**. Fare clic sul pulsante **Espressione** (*fx*) per modificare l'espressione.  
  
> [!NOTE]  
>  Se è disponibile una query compilata in una finestra di progettazione query, il relativo testo verrà visualizzato in questa casella.  
  
 **Nome tabella**  
 Immettere il nome della tabella che si desidera utilizzare come set di dati. Questa opzione viene visualizzata quando si seleziona **Tabella**.  
  
 **Selezionare o immettere un nome di stored procedure**  
 Digitare o scegliere il nome della stored procedure che si desidera utilizzare. Fare clic sul pulsante **Espressione** (*fx*) per modificare l'espressione. Questa opzione viene visualizzata quando si sceglie l'opzione del tipo di comando Stored procedure.  
  
 **Timeout (in secondi)**  
 Consente di digitare il numero di secondi di attesa prima del timeout della query. Il valore predefinito è 30 secondi. Il valore nel campo **Timeout** deve essere vuoto o maggiore di zero. Se non si specifica alcun valore, non si verificherà mai il timeout della query.  
  
 **Aggiorna campi**  
 Eseguire il comando di query per aggiornare l'elenco di campi nella pagina [Finestra di dialogo Proprietà set di dati, Campi](http://msdn.microsoft.com/library/75c7e54a-3d20-4c9a-88da-ab36dce2ce42) .  
  
## <a name="see-also"></a>Vedere anche  
 [Set di dati del report &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Guida di Generatore report per finestre di dialogo, riquadri e procedure guidate](http://msdn.microsoft.com/en-us/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Finestre di progettazione query &#40;Generatore report&#41;](http://msdn.microsoft.com/library/553f0d4e-8b1d-4148-9321-8b41a1e8e1b9)  
  
  
