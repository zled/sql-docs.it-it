---
title: Avviare Generatore Report (Generatore Report) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
caps.latest.revision: 50
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: c2802b0ed89de430e892baacdd8ec3dfce8485c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227011"
---
# <a name="start-report-builder-report-builder"></a>Avviare Generatore report (Generatore report).
  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] include autonomo e [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] versioni di Generatore Report. È possibile utilizzare la versione [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installato in modalità nativa o in modalità integrata SharePoint.  
  
> [!NOTE]  
>  Generatore report non può essere installato in computer basati sul processore Itanium 64. Questo vale per il [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] e nelle versioni autonome di Generatore Report.  
  
 Se la versione [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] di Generatore report avviata è una versione precedente, contattare l'amministratore, che potrà aggiornare Gestione report e il sito di SharePoint per consentire l'utilizzo della versione [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] di Generatore report.  
  
 È possibile utilizzare anche la versione [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] di Generatore report per creare report nella cartella di lavoro [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] pubblicata su SharePoint. Per altre informazioni sull'utilizzo di Generatore Report con [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], vedere [creare un Report di Reporting Services con i dati PowerPivot](http://go.microsoft.com/fwlink/?LinkId=185238) sul sito Web technet.microsoft.com.  
  
 Per avviare autonoma di Generatore Report le **avviare** menu nel computer locale, utente o un amministratore deve installare Generatore Report direttamente nel computer prima che lo strumento è disponibile per l'utilizzo. La versione autonoma non viene installata quando si installa [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ma è necessario scaricarla e installarla separatamente. Per scaricare Generatore Report, vedere [Generatore Report di Microsoft® SQL Server® 2012](http://go.microsoft.com/fwlink/?LinkId=401502).  
  
### <a name="to-start-report-builder-clickonce-from-report-manager"></a>Per avviare Generatore report ClickOnce da Gestione report  
  
1.  Digitare l'URL per il server di report nella barra degli indirizzi del browser. L'URL predefinito è http://\<*nomeserver*>/reports. Verrà aperto Gestione report.  
  
2.  Fare clic su **Generatore report**.  
  
     Verrà avviato Generatore report e sarà possibile creare un report o aprire un report nel server di report.  
  
### <a name="to-start-report-builder-clickonce-using-a-url"></a>Per avviare Generatore report ClickOnce tramite un URL  
  
1.  Nella barra degli indirizzi del browser digitare l'URL seguente:  
  
     http://\<servername > /reportserver/reportbuilder/ReportBuilder_3_0_0_0.application  
  
2.  Premere INVIO.  
  
     Verrà avviato Generatore report e sarà possibile creare un report o aprire un report nel server di report.  
  
### <a name="to-start-report-builder-clickonce-in-sharepoint-integrated-mode"></a>Per avviare Generatore report ClickOnce in modalità integrata SharePoint  
  
1.  Accedere al sito di SharePoint che contiene la raccolta desiderata.  
  
2.  Aprire la raccolta.  
  
3.  Fare clic su **Documenti**.  
  
4.  Scegliere **Report di Generatore report** dal menu **Nuovo documento**.  
  
     Verrà avviato Generatore report e sarà possibile creare un report o aprire un report nel server di report.  
  
     **Nota** se il **nuovo documento** menu non sono elencati i **Report di Generatore Report**, **modello di Generatore Report**, e **originedatidelReport** le opzioni, i tipi di contenuto devono essere aggiunti alla raccolta di SharePoint. Per altre informazioni, vedere [aggiungere tipi di contenuto in una raccolta di &#40;Reporting Services in modalità integrata SharePoint&#41; ](../add-reporting-services-content-types-to-a-sharepoint-library.md) nelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [documentazione Online di](http://go.microsoft.com/fwlink/?LinkId=154888) in sito Web MSDN.microsoft.com.  
  
### <a name="to-start-report-builder-stand-alone-from-the-start-menu"></a>Per avviare la versione autonoma di Generatore report dal menu Start  
  
1.  Nel menu Start, fare clic su **tutti i programmi**, quindi fare clic su [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] **Generatore Report**.  
  
2.  Fare clic su **Generatore report** .  
  
     Verrà visualizzato Generatore report e sarà possibile creare o aprire un report.  
  
3.  Per creare un nuovo report, fare clic sull'icona di SQL Server nell'angolo superiore sinistro di Generatore report, quindi fare clic su Nuovo.  
  
4.  Per aprire un report esistente archiviato nel computer locale o in un server di report, fare clic sull'icona di SQL Server nell'angolo superiore sinistro di Generatore report, quindi fare clic su Apri.  
  
     Se il server di report nell'elenco dei server esistenti non visibile, chiudere la **Apri Report** finestra di dialogo e quindi fare clic su **Connect** nella parte inferiore di Generatore Report e connettersi al server.  
  
## <a name="see-also"></a>Vedere anche  
 [Generatore report in SQL Server 2014](report-builder-in-sql-server-2016.md)  
  
  
