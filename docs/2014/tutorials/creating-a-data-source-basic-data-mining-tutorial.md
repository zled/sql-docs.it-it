---
title: Creazione di un'origine dati (esercitazione di base di Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7107c32-69ed-49a8-9b6e-32753eebf42c
caps.latest.revision: 51
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b86c10563ffae3073b92373eec5e07c18c1c0668
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312589"
---
# <a name="creating-a-data-source-basic-data-mining-tutorial"></a>Creazione di un'origine dati (Esercitazione di base sul data mining)
  Un *origine dati* è una connessione dati salvata e gestita del progetto e distribuita i [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database. L'origine dati contiene il nome del server e del database in cui si trovano i dati di origine in aggiunta ad altre proprietà di connessione necessarie.  
  
> [!IMPORTANT]  
>  Il nome del database è [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]. Se non è già installato il database, vedere la [Microsoft SQL Sample Databases](http://go.microsoft.com/fwlink/?LinkId=88417) pagina.  
  
### <a name="to-create-a-data-source"></a>Per creare un'origine dati  
  
1.  In **Esplora soluzioni**, fare doppio clic sul **origini** cartella e selezionare **nuova origine dati**.  
  
2.  Nel **Creazione guidata origine dati** fare clic su **successivo**.  
  
3.  Nel **selezionare la modalità di definizione connessione** pagina, fare clic su **New** per aggiungere una connessione per il [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.  
  
4.  Nel **Provider** nell'elenco **Connection Manager**, selezionare **OLE DB nativo\sql Server Native Client 11.0**.  
  
5.  Nel **nome del Server** digitare o selezionare il nome del server in cui è installato [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].  
  
     Ad esempio, digitare **localhost** se il database è ospitato nel server locale.  
  
6.  Nel **accedere al server** gruppo, selezionare **Usa autenticazione di Windows**.  
  
    > [!IMPORTANT]  
    >  Se possibile, gli implementatori devono utilizzare l'autenticazione di Windows, che fornisce un metodo di autenticazione più sicuro rispetto all'autenticazione di SQL Server. Tuttavia, l'autenticazione di SQL Server è disponibile per la compatibilità con le versioni precedenti. Per ulteriori informazioni sui metodi di autenticazione, vedere [configurazione del motore di Database - Provisioning Account](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md).  
  
7.  Nel **selezionare o immettere un nome di database** elenco, selezionare [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] e quindi fare clic su **OK**.  
  
8.  Scegliere **Avanti**.  
  
9. Nel **le informazioni sulla rappresentazione** fare clic su **utilizzare l'account del servizio**e quindi fare clic su **Avanti**.  
  
     Nel **Completamento procedura guidata** pagina, si noti che, per impostazione predefinita, l'origine dati è denominata Adventure Works DW 2012.  
  
10. Fare clic su **Fine**.  
  
     La nuova origine dati, Adventure Works DW 2012, viene visualizzato nel **origini dati** cartella in Esplora soluzioni.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Creazione di dati di un vista origine &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Attività precedente della lezione  
 [Creazione di un'analisi di progetto di servizi &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un'origine dati &#40;SSAS multidimensionale&#41;](../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md)   
 [Definizione di un'origine dati](../analysis-services/lesson-1-2-defining-a-data-source.md)   
 [Impostare le opzioni di rappresentazione &#40;SSAS - multidimensionale&#41;](../analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional.md)  
  
  