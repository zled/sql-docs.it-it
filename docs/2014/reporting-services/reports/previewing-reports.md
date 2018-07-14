---
title: Anteprima dei report | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], previewing reports
- previewing reports [Reporting Services]
- printing previews
- test servers [Reporting Services]
ms.assetid: 85117f6c-828e-45c9-810f-e700d9bfba67
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: afcfb2cf31526f4e8898fafbe72f9492a1848886
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202531"
---
# <a name="previewing-reports"></a>Anteprima dei report
  Durante la progettazione di un report, potrebbe essere necessario visualizzarlo prima di pubblicarlo in un ambiente di produzione. Tale operazione può essere eseguita passando alla modalità di anteprima in Progettazione report, utilizzando la finestra di anteprima in Progettazione report e pubblicando il report in un server di report in un ambiente di prova.  
  
> [!NOTE]  
>  Quando un report viene visualizzato in anteprima, i dati per il report vengono memorizzati nella cache in un file nel computer locale. Quando lo stesso report viene visualizzato di nuovo in anteprima utilizzando la stessa query, gli stessi parametri e le stesse credenziali, in Progettazione report viene recuperata la copia memorizzata nella cache anziché rieseguire la query. Il file di dati viene salvato come *\<nomereport>*.rdl.data nella stessa directory del file di definizione del report. e non viene eliminato alla chiusura di Progettazione report.  
  
## <a name="preview-mode"></a>Modalità di anteprima  
 È possibile visualizzare in anteprima un report in Progettazione Report facendo clic **Preview**. Il report verrà eseguito localmente, utilizzando le stesse funzionalità di elaborazione e rendering del report offerte dal server di report. Il report visualizzato è un'immagine interattiva. È quindi possibile selezionare parametri, fare clic sui collegamenti, visualizzare la mappa documento ed espandere e comprimere le aree nascoste del report. È inoltre possibile esportare il report in uno dei formati di rendering installati.  
  
## <a name="standalone-preview"></a>Anteprima autonoma  
 Per visualizzare in anteprima un report è possibile inoltre eseguire il progetto report in una configurazione per il debug, ad esempio per eseguire il debug degli assembly personalizzati scritti. Per eseguire un progetto sono disponibili tre modi:  
  
-   Facendo clic **avviare** nel **Debug** menu.  
  
-   Facendo clic la **avviare** pulsante la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] barra degli strumenti standard.  
  
-   Premere F5.  
  
 Se si usa una configurazione di progetto che compila il report senza distribuirlo, il report specificato nella `StartItem` proprietà della configurazione corrente viene aperto in una finestra di anteprima distinta. La visualizzazione e la funzionalità del report nella finestra di anteprima sono uguali a quelle della modalità di anteprima.  
  
> [!NOTE]  
>  Prima di eseguire il debug di un report è necessario impostare un elemento iniziale. Per impostare un elemento iniziale, in Esplora soluzioni, fare clic sul progetto report, fare clic su **delle proprietà**, quindi nel `StartItem`, selezionare il nome del report da visualizzare.  
  
 Se si desidera visualizzare in anteprima un report che non è l'elemento iniziale del progetto, selezionare una configurazione che compili il report senza distribuirlo, ad esempio la configurazione DebugLocal. Fare clic con il pulsante destro del mouse sul report e quindi scegliere **Esegui**. È necessario scegliere una configurazione che non preveda la distribuzione del report. In caso contrario, il report verrà pubblicato nel server di report anziché venire visualizzato in locale in una finestra di anteprima.  
  
## <a name="print-preview"></a>Anteprima di stampa  
 La prima volta che viene visualizzato in modalità di anteprima o nella finestra di anteprima, il report è simile a quello generato dall'estensione per il rendering HTML. L'anteprima non è in formato HTML, ma il layout e la paginazione del report sono simili a quelli dell'output HTML.  
  
 Se si passa alla modalità anteprima di stampa, è possibile visualizzare la rappresentazione del report stampato. Fare clic sul pulsante **Anteprima di stampa** sulla barra degli strumenti di anteprima. Il report verrà visualizzato come in una pagina fisica. Questa visualizzazione assomiglia all'output generato dalle estensioni per il rendering delle immagini e PDF. L'anteprima di stampa non è un'immagine né un file PDF, ma la paginazione e il layout del report sono simili a quelli dell'output in questi formati.  
  
## <a name="publishing-to-a-test-server"></a>Pubblicazione in un server di prova  
 È inoltre possibile eseguire testare i report pubblicandoli in un server di prova. La pubblicazione di un report in un server di prova è analoga alla pubblicazione di un report in un server di produzione. Per informazioni sulla pubblicazione di un report, vedere [Pubblicazione dei report in un server di report](publishing-reports-to-a-report-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Stampa di report &#40;Generatore report e SSRS&#41;](../report-builder/print-reports-report-builder-and-ssrs.md)   
 [Stampare un report &#40;Generatore report e SSRS&#41;](../report-builder/print-a-report-report-builder-and-ssrs.md)   
 [Pubblicazione di report](../publish-reports.md)   
 [Uso di assembly personalizzati con i report](../custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
