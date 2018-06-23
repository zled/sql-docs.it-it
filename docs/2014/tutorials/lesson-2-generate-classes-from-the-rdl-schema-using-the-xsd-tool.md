---
title: 'Lezione 2: Generare classi dallo Schema RDL mediante lo strumento xsd | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
caps.latest.revision: 13
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 67cbc84882683fcb31d6b42f69274d5166556450
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170254"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a>Lezione 2: Generazione delle classi dallo schema RDL mediante lo strumento xsd
  Dopo aver creato il progetto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è necessario recuperare una copia locale dello schema di definizione del report ed eseguire lo strumento per la definizione di XML Schema (Xsd.exe).  
  
### <a name="to-generate-the-rdl-classes"></a>Per generare le classi RDL  
  
1.  Aprire un'istanza di [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer (o un browser equivalente) e passare all'URL seguente:  
  
    ```  
    http://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  Dopo aver aperto lo schema RDL nel browser, passare il **File** dal menu **Salva con nome**.  
  
3.  Passare al percorso in cui è stato creato il progetto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e salvare lo schema con il nome ReportDefinition.xsd.  
  
4.  Dopo aver salvato il file, aprire un'istanza del [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] prompt dei comandi. Per aprire un'istanza del prompt dei comandi, fare clic sul menu Start, scegliere **tutti i programmi**, scegliere **Microsoft Visual Studio 2010**, scegliere **strumenti di Visual Studio** e fare clic su **Prompt dei comandi di visual Studio (2010)**.  
  
5.  Modificare il percorso corrente sul percorso in cui è stato salvato il file ReportDefinition.xsd:  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  Generare il file ReportDefinition.cs che contiene le classi per lo schema RDL con il comando seguente:  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     Per generare il file ReportDefinition.vb utilizzare il comando seguente:  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  Aggiungere il progetto ReportDefinition.xsd. Dal **Project** menu, fare clic su **Aggiungi elemento esistente**. Selezionare il percorso del file Reportdefinition XSD, selezionare reportdefinition. xsd e fare clic su **Aggiungi**.  
  
    > [!NOTE]  
    >  Dopo aver aggiunto il file Reportdefinition XSD al progetto si noterà **Esplora soluzioni** che il file ReportDefinition.cs (con estensione vb) non è presente. Per visualizzare il file, fare clic sul pulsante per espandere/comprimere accanto al file ReportDefinition.xsd.  
  
## <a name="next-lesson"></a>Lezione successiva  
 Nella lezione successiva verrà scritto codice per caricare la definizione di un report da un server di report utilizzando le classi generate dallo schema RDL. Vedere [lezione 3: caricare una definizione del Report dal Server di Report](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [L'aggiornamento di report mediante le classi generate dallo Schema RDL &#40;esercitazione su SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Report Definition Language &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  