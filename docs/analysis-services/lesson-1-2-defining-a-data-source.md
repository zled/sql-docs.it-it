---
title: Definizione di un'origine dati | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 5a3e83c9-8788-431e-85b0-a68c79377ff3
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: d54f8f04c4e67a81fc1da4c47c6e995ac98ff84d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-1-2---defining-a-data-source"></a>Lezione 1-2-definizione di un'origine dati
Dopo aver creato un progetto di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , la prima operazione consiste nel definire una o più origini dati da usare. Quando si definisce un'origine dei dati si specificano le informazioni sulla stringa di connessione che verrà utilizzata per connettersi all'origine dei dati. Per altre informazioni, vedere [Creare un'origine dati &#40;SSAS multidimensionale&#41;](../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md).  
  
Nell'attività seguente il database di esempio AdventureWorksDWSQLServer2012 verrà definito come origine dati del progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial. Ai fini di questa esercitazione questo database si trova nel computer locale. Tuttavia, i database di origine sono spesso ospitati in uno o più computer remoti.  
  
### <a name="to-define-a-new-data-source"></a>Per definire una nuova origine dati  
  
1.  In Esplora soluzioni (a destra della finestra di Microsoft Visual Studio) fare clic con il pulsante destro del mouse su **Origini dati**, quindi scegliere **Nuova origine dati**.  
  
2.  Nel **la creazione guidata origine dati** pagina del **Creazione guidata origine dati**, fare clic su **Avanti** per aprire la **selezionare la modalità di definizione connessione**pagina.  
  
3.  Nella pagina **Selezione metodo di definizione connessione** è possibile definire un'origine dati basata su una nuova connessione, su una connessione esistente o su un oggetto origine dati definito in precedenza. In questa esercitazione verranno illustrate le procedure per definire un'origine dati basata su una nuova connessione. Verificare che l'opzione **Crea un'origine dati basata su una connessione nuova o esistente** sia selezionata e fare clic su **Nuova**.  
  
4.  Nella finestra di dialogo **Gestione connessione** si definiscono le proprietà di connessione per l'origine dati. Nella casella di riepilogo **Provider** verificare che l'opzione **OLE DB nativo\SQL Server Native Client 11.0** sia selezionata.  
  
    [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supporta anche gli altri provider visualizzati nell'elenco **Provider** .  
  
5.  Nella casella di testo **Nome server** digitare **localhost**.  
  
    Per connettersi a un'istanza denominata sul computer locale, digitare **localhost\\<instance name>**. Per connettersi al computer specifico anziché al computer locale, digitare il nome o l'indirizzo IP del computer.  
  
6.  Verificare che l'opzione **Usa autenticazione di Windows** sia selezionata. Nell'elenco **Selezionare o immettere un nome di database** selezionare **AdventureWorksDW2012**.  
  
7.  Fare clic su **Test connessione** per testare la connessione al database.  
  
8.  Fare clic su **OK**e quindi su **Avanti**.  
  
9. Nella pagina **Impostazioni di rappresentazione** della procedura guidata si definiscono le credenziali di sicurezza per [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] necessarie per connettersi all'origine dati. La rappresentazione influisce sull'account di Windows utilizzato per connettersi all'origine dati quando è selezionata l'autenticazione di Windows. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] non supporta la rappresentazione per l'elaborazione di oggetti OLAP. Selezionare **Usa account del servizio**e quindi fare clic su **Avanti**.  
  
10. Nella pagina **Completamento procedura guidata** accettare il nome predefinito **Adventure Works DW 2012**e fare clic su **Fine** per creare la nuova origine dati.  
  
> [!NOTE]  
> Per modificare le proprietà dell'origine dati dopo che è stata creata, fare doppio clic su di essa nella cartella **Origini dati** per visualizzarne le proprietà in **Progettazione origine dati**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Definizione di una vista origine dati](../analysis-services/lesson-1-3-defining-a-data-source-view.md)  
  
## <a name="see-also"></a>Vedere anche  
[Creare un'origine dati &#40;SSAS multidimensionale&#41;](../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md)  
  
