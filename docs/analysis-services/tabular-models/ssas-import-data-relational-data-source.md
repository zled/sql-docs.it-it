---
title: Importare da un'origine dati relazionale (SSAS tabulare) | Documenti Microsoft
ms.custom: 
ms.date: 05/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1db6dd24d059f8c478967bc3c69652aaec0aeb51
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="import-data---relational-data-source"></a>Importazione dei dati - origine dati relazionale
  Tramite Importazione guidata tabella è possibile importare dati da un'ampia gamma di database relazionali. La procedura guidata è disponibile in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dal menu **Modello** . Per connettersi a un'origine dati, è necessario che nel computer sia installato il provider appropriato. Per altre informazioni su origini dati e provider supportati, vedere [Origini dati supportate &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md).  
  
 L'Importazione guidata tabella supporta l'importazione di dati dalle origini dati seguenti:  
  
 **Database relazionali**  
  
-   Database di Microsoft SQL Server  
  
-   Microsoft SQL Azure  
  
-   Database di Microsoft Access  
  
-   Microsoft SQL Server Parallel Data Warehouse  
  
-   Oracle  
  
-   Teradata  
  
-   Sybase  
  
-   Informix  
  
-   IBM DB2  
  
-   OLE DB/ODBC  
  
 **Origini multidimensionali**  
  
-   Cubo di Microsoft SQL Server Analysis Services  
  
 L'Importazione guidata tabella non supporta l'importazione di dati da una cartella di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] come origine dati.  
  
### <a name="to-import-data-from-a-database"></a>Per importare dati da un database  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]fare clic sul menu **Modello** , quindi selezionare **Importa da origine dati**.  
  
2.  Nella pagina **Connessione a un'origine dati** selezionare il tipo di database a cui connettersi, quindi fare clic su **Avanti**.  
  
3.  Seguire i passaggi nell'Importazione guidata tabella. Nelle pagine successive, sarà possibile selezionare tabelle e viste specifiche o applicare filtri tramite la pagina **Selezione tabelle e viste** oppure creando una query SQL nella pagina **Specifica di una query SQL** .  
  
## <a name="see-also"></a>Vedere anche  
 [Importare dati &#40;SSAS tabulare&#41;](http://msdn.microsoft.com/library/6617b2a2-9f69-433e-89e0-4c5dc92982cf)   
 [Origini dati supportate &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
