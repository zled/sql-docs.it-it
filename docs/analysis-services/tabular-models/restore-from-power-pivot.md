---
title: Eseguire il ripristino da PowerPivot | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 88cd0379f0d23f819ab362a273c58bb40db81fa9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="restore-from-power-pivot"></a>Eseguire il ripristino da PowerPivot
  È possibile usare la funzionalità Ripristina da [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in SQL Server Management Studio per creare un nuovo database modello tabulare in un'istanza di Analysis Services in esecuzione in modalità tabulare oppure per eseguire il ripristino a un database esistente da una cartella di lavoro con estensione xlsx di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
> [!NOTE]  
>  Il modello di progetto Importa da [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in SQL Server Data Tools offre funzionalità simili. Per altre informazioni, vedere [Importare da Power Pivot &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md).  
  
 Quando si usa Ripristina da [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], tenere presente quanto segue:  
  
-   Per poter usare Ripristina da [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], è necessario aver eseguito l'accesso come membro del ruolo di amministratori del server nell'istanza di Analysis Services.  
  
-   L'account del servizio dell'istanza di Analysis Services deve disporre di autorizzazioni di lettura per il file della cartella di lavoro da cui eseguire il ripristino.  
  
-   Per impostazione predefinita, quando si ripristina un database da [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], la proprietà Impostazioni di rappresentazione origine dati del database modello tabulare è impostata sul valore predefinito, che specifica l'account del servizio dell'istanza di Analysis Services. Si consiglia di impostare le credenziali di rappresentazione su un account utente di Windows nelle proprietà del database. Per altre informazioni, vedere [Rappresentazione &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/impersonation-ssas-tabular.md).  
  
-   I dati nel modello di dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] vengono copiati in un database modello tabulare nuovo o esistente nell'istanza di Analysis Services. Se la cartella di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] contiene tabelle collegate, queste verranno ricreate come tabelle senza origine dati, analogamente alle tabelle create con Incolla in nuova tabella.  
  
### <a name="to-restore-from-power-pivot"></a>Per eseguire il ripristino da PowerPivot  
  
1.  Nell'istanza di Active Directory di SSMS in cui si vuole eseguire il ripristino fare clic con il pulsante destro del mouse su **Database** e quindi scegliere **Ripristina da [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**.  
  
2.  In **File di backup** in **Origine ripristino** nella finestra di dialogo **Ripristina da [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]** fare clic su **Sfoglia**, quindi selezionare un file con estensione xslx o abf da cui eseguire il ripristino.  
  
3.  In **Destinazione ripristino**in **Ripristina database**digitare un nome per un nuovo database o per uno esistente. Se non si specifica un nome, viene utilizzato quello della cartella di lavoro.  
  
4.  In **Percorso di archiviazione**fare clic su **Sfoglia**, quindi selezionare un percorso per l'archiviazione del database.  
  
5.  Nella casella **Opzioni**lasciare **Includi informazioni di sicurezza** selezionato. Quando si esegue il ripristino da una cartella di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , questa impostazione non è applicabile.  
  
## <a name="see-also"></a>Vedere anche  
 [Database modello tabulare &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)   
 [Importare da Power Pivot &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)  
  
  
