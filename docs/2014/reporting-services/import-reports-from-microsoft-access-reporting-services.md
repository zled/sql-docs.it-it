---
title: Importare report da Microsoft Access (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dc63daf4095238f948be6bde22bf190aa4d1977a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086507"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Importazione report da Microsoft Access (Reporting Services)
  In Progettazione Report, è possibile importare report da un [!INCLUDE[msCoName](../includes/msconame-md.md)] database di Access o project. A tale scopo è necessario che Access 2002 o versione successiva sia installato nello stesso computer in cui è installato Progettazione report.  
  
 Con la caratteristica di importazione vengono importati tutti i report inclusi nel progetto o nel database. Se il file di Access include molti report, è possibile creare un progetto report separato per l'importazione e quindi aprire i singoli file RDL nel progetto report principale. È possibile modificare i report dopo l'importazione in Progettazione report.  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non supporta tutti gli oggetti report di Access. Gli elementi che non vengono convertiti vengono visualizzati nei **elenco attività** finestra. Per altre informazioni, vedere [funzionalità supportate di accesso Report &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).  
  
### <a name="to-import-reports-from-microsoft-access"></a>Per importare report da Microsoft Access  
  
1.  Aprire o creare un progetto in cui importare i report.  
  
2.  Nel **progetto** dal menu **Importa report**, quindi fare clic su **Microsoft Access**. In alternativa, fare clic sul progetto in Esplora soluzioni, scegliere **Importa report**, quindi fare clic su **Microsoft Access**.  
  
3.  Nel **aperto** finestra di dialogo, selezionare il database di Access (file con estensione mdb, accdb) o un progetto (con estensione adp) che contiene i report e quindi fare clic su **Open**. Tutti i report contenuti nel file di progetto o di database verranno importati ed elencati nella cartella Report in Esplora soluzioni.  
  
4.  Verificare i **elenco attività** finestra per errori di compilazione. Per visualizzare il **elenco attività** finestra, aprire il **visualizzazione** dal menu **Other Windows**, quindi fare clic su **elenco attività**.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettare report con Progettazione report &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
