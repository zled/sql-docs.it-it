---
title: Finestre Progettazione Query di Reporting Services | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- query designers [Reporting Services]
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
caps.latest.revision: 16
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: ca805856f4cd09d6d1172b5602a7a9e54b4cc16c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062588"
---
# <a name="reporting-services-query-designers"></a>Strumenti di progettazione query in Reporting Services
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sono incluse finestre Progettazione query con interfaccia grafica e basata su testo per la compilazione di query per ogni tipo di origine dati nel report.  
  
 Alcune origini dati supportano finestre di progettazione che consentono di compilare in modo interattivo una query. Altre origini dati utilizzano una finestra Progettazione query basata su testo. La finestra Progettazione query con interfaccia grafica consente di trascinare gli elementi dei metadati che rappresentano i dati sottostanti in un'origine dati nell'area di progettazione della query. Nella finestra Progettazione query basata su testo è possibile digitare il testo del comando in un apposito riquadro, Per passare dalla finestra Progettazione query con interfaccia grafica a quella basata su testo, fare clic sull'icona relativa a quest'ultima sulla barra degli strumenti.  
  
 I tipi di origine dati disponibili nel report sono determinati dalle estensioni per i dati di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installate nel client o nel server di report. Per altre informazioni, vedere [File di configurazione RSReportDesigner](report-server/rsreportdesigner-configuration-file.md) e [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).  
  
 Un'estensione per l'elaborazione dati e la relativa finestra Progettazione query possono presentare differenze per quanto riguarda il supporto delle origini dati nei modi seguenti:  
  
-   **In base al tipo di finestra Progettazione query** Ad esempio, un'origine dati [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] supporta entrambi i tipi di progettazione, con interfaccia grafica e basata su testo.  
  
-   **In base alla differenza nel linguaggio di query.** Un linguaggio di query come [!INCLUDE[tsql](../includes/tsql-md.md)] , ad esempio, può presentare differenze nella sintassi a seconda del tipo di origine dati, mentre la sintassi dei linguaggi [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] e Oracle SQL presenta alcune differenze in un comando di query.  
  
-   **In base al supporto per la parte indicante lo schema di un nome di oggetto di database.** Se un'origine dei dati prevede l'utilizzo degli schemi negli identificatori di oggetto di database, è necessario specificare il nome dello schema nella query per gli eventuali nomi che non utilizzano lo schema predefinito. Ad esempio, `SELECT FirstName, LastName FROM [Person].[Person]`.  
  
-   **In base al supporto per i parametri di query.** Il supporto dei parametri varia a seconda del provider di dati. Alcuni provider di dati supportano i parametri denominati, ad esempio `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`. Altri supportano invece i parametri senza nome, ad esempio `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`. Identificatore del parametro potrebbero essere diversi dal provider di dati; ad esempio, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizza il "at" (@) simbolo, Oracle Usa i due punti (:). Alcuni provider di dati non supportano parametri.  
  
-   **In base alla possibilità di importare query.** Per un'origine dati [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è ad esempio possibile importare una query da un file di definizione di report (con estensione rdl) o da un file sql.  
  
## <a name="query-designers"></a>Finestre di progettazione query  
 Negli argomenti seguenti viene descritta l'interfaccia utente di ogni finestra Progettazione query.  
  
-   [Interfaccia utente di Progettazione query MDX di Analysis Services](report-data/analysis-services-mdx-query-designer-user-interface.md)  
  
-   [Interfaccia utente di Progettazione query DMX in Analysis Services](report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
-   [Interfaccia utente della finestra Progettazione query con interfaccia grafica](report-data/graphical-query-designer-user-interface.md)  
  
-   [Interfaccia utente di Progettazione query relazionale](../../2014/reporting-services/relational-query-designer-user-interface.md)  
  
-   [Interfaccia utente di Progettazione query Hyperion Essbase](report-data/hyperion-essbase-query-designer-user-interface.md)  
  
-   [Interfaccia utente della finestra Progettazione query del modello di report](report-data/report-model-query-designer-user-interface.md)  
  
-   [Interfaccia utente di Progettazione query SAP NetWeaver BI](report-data/sap-netweaver-bi-query-designer-user-interface.md)  
  
-   [Progettazione query di elenco di SharePoint](../../2014/reporting-services/sharepoint-list-query-designer.md)  
  
-   [Interfaccia utente di Progettazione query basata su testo](../../2014/reporting-services/text-based-query-designer-user-interface.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Origini dati supportate da Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Aggiungere dati da origini dati esterne &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md)   
 [Estensioni per l'elaborazione dati e provider di dati .NET Framework &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md)   
 [Le estensioni &#40;SSRS&#41;](extensions-ssrs.md)  
  
  