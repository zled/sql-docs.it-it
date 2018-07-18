---
title: Importare i dati (SSAS tabulare) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6617b2a2-9f69-433e-89e0-4c5dc92982cf
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 35312647eeb1b452c155c05d7f4392fa540aa156
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253563"
---
# <a name="import-data-ssas-tabular"></a>Importare dati (SSAS tabulare)
  È possibile importare dati in un modello tabulare da diverse origini. Negli argomenti contenuti in questa sezione viene descritto come utilizzare l'Importazione guidata dati in Progettazione modelli per connettersi ai dati e selezionare quelli da importare in un progetto di modello.  
  
> [!IMPORTANT]  
>  Se una tabella nel modello conterrà un numero considerevole di righe, si consideri di importare solo un subset dei dati durante la creazione di modelli. L'importazione di un subset dei dati consente di ridurre tempi di elaborazione e utilizzo delle risorse server per il database dell'area di lavoro.  
  
 L'Importazione guidata tabella consente di importare i dati dalle origini dati seguenti:  
  
|**Data Source**|**Descrizione**|  
|---------------------|---------------------|  
|**Database relazionali**|Tra le origini dati relazionali sono incluse:<br /><br /> Microsoft SQL Server<br /><br /> Microsoft SQL Azure<br /><br /> Microsoft SQL Server Parallel Data Warehouse<br /><br /> Microsoft Access<br /><br /> Oracle<br /><br /> Teradata<br /><br /> Sybase<br /><br /> Informix<br /><br /> IBM DB2<br /><br /> OLEDB/ODBC|  
|**Origini multidimensionali**|Cubo di Microsoft SQL Server Analysis Services|  
|**Feed di dati**|Tra i feed di dati sono inclusi:<br /><br /> Report di Microsoft Reporting Services<br /><br /> Set di dati di Azure DataMarket<br /><br /> Feed Atom da un provider pubblico o aziendale|  
|**File di testo**|Tra i file di testo sono inclusi:<br /><br /> File di Excel (con estensione xlsx)<br /><br /> File di testo (con estensione txt)|  
  
 Oltre all'importazione di dati tramite l'Importazione guidata tabella, è possibile incollare dati copiati (dagli Appunti) in una tabella del modello. Il comportamento dei dati incollati differisce da quello dei dati importati da altre origini dati. I dati incollati nelle tabelle non dispongono di una proprietà Nome connessione o Origine dati. I dati incollati sono persistenti nel file Model.bim. Quando il progetto o il file Model.bim viene salvato, anche i dati incollati vengono salvati.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Importare da un'origine dati relazionale &#40;tabulare di SSAS&#41;](import-from-a-relational-data-source-ssas-tabular.md)|Viene descritto come importare dati da origini dati relazionali quali un database di Microsoft SQL Server, Oracle o Teradata.|  
|[Importa da un'origine dati multidimensionale &#40;tabulare di SSAS&#41;](import-from-a-multidimensional-data-source-ssas-tabular.md)|Viene descritto come importare dati da un cubo multidimensionale di SQL Server Analysis Services.|  
|[Importare da un Feed di dati &#40;tabulare di SSAS&#41;](import-from-a-data-feed-ssas-tabular.md)|Viene descritto come importare dati da un feed di dati quale un report di Microsoft Reporting Services o un set di dati di Azure DataMarket.|  
|[Importa da un File di testo &#40;tabulare di SSAS&#41;](import-from-a-text-file-ssas-tabular.md)|Viene descritto come importare dati da una cartella di lavoro di Microsoft Excel o da un file di testo.|  
|[Copiare e incollare i dati &#40;tabulare di SSAS&#41;](copy-and-paste-data-ssas-tabular.md)|Viene descritto come aggiungere dati a una tabella esistente in Progettazione modelli tramite Incolla e Accoda il contenuto degli Appunti.|  
  
  
