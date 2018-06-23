---
title: Importare report da Microsoft Access (Reporting Services) | Documenti Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
caps.latest.revision: 39
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: ec0461f278bfe6556d4a1fa221d5b33426d8ed01
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156871"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Importazione report da Microsoft Access (Reporting Services)
  In Progettazione Report, è possibile importare report da un [!INCLUDE[msCoName](../includes/msconame-md.md)] database di Access o project. A tale scopo è necessario che Access 2002 o versione successiva sia installato nello stesso computer in cui è installato Progettazione report.  
  
 Con la caratteristica di importazione vengono importati tutti i report inclusi nel progetto o nel database. Se il file di Access include molti report, è possibile creare un progetto report separato per l'importazione e quindi aprire i singoli file RDL nel progetto report principale. È possibile modificare i report dopo l'importazione in Progettazione report.  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non supporta tutti gli oggetti report di Access. Gli elementi che non vengono convertiti vengono visualizzati i **elenco attività** finestra. Per altre informazioni, vedere [supportato l'accesso alle funzionalità di Report &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).  
  
### <a name="to-import-reports-from-microsoft-access"></a>Per importare report da Microsoft Access  
  
1.  Aprire o creare un progetto in cui importare i report.  
  
2.  Nel **Project** dal menu **Importa report**, quindi fare clic su **Microsoft Access**. In alternativa, fare clic sul progetto in Esplora soluzioni, scegliere **Importa report**, quindi fare clic su **Microsoft Access**.  
  
3.  Nel **Open** finestra di dialogo, selezionare il database di Access (mdb, accdb) o il progetto (con estensione adp) che contiene i report e quindi fare clic su **Apri**. Tutti i report contenuti nel file di progetto o di database verranno importati ed elencati nella cartella Report in Esplora soluzioni.  
  
4.  Controllare la **elenco attività** finestra per errori di compilazione. Per visualizzare il **elenco attività** finestra, aprire il **vista** dal menu **altre finestre**, quindi fare clic su **elenco attività**.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettare report con Progettazione report &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  