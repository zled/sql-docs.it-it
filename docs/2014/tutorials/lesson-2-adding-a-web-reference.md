---
title: 'Lezione 2: Aggiunta di un riferimento Web | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a2c2b8b8-6b13-45ca-ab3b-1582447b6807
caps.latest.revision: 29
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ff0efdd840ee2f4efb0da802da64494640911b80
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275627"
---
# <a name="lesson-2-adding-a-web-reference"></a>Lezione 2: Aggiunta di un riferimento Web
  L'individuazione di un servizio Web è il processo che consente a un client di individuare un servizio Web e ottenerne la descrizione. Il processo di individuazione di un servizio Web in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] implica l'interrogazione di un sito Web in base a un algoritmo predeterminato. Scopo di questo processo è quello di individuare la descrizione del servizio, ovvero un documento XML scritto nel linguaggio WSDL (Web Services Description Language).  
  
 Nella descrizione del servizio vengono indicati i servizi disponibili e le modalità di interazione con tali servizi. Senza una descrizione del servizio non è possibile interagire con un servizio Web a livello di programmazione.  
  
 L'applicazione deve disporre di un mezzo per comunicare con il servizio Web e per individuarlo in fase di esecuzione. Questo risultato si ottiene tramite l'aggiunta di un riferimento Web al progetto del servizio Web, operazione che consente di generare una classe proxy che si interfaccia con il servizio Web e ne fornisce una rappresentazione locale. Per ulteriori informazioni, vedere gli argomenti relativi alla generazione di un proxy del servizio Web XML nella documentazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="to-add-a-web-reference"></a>Per aggiungere un riferimento Web  
  
1.  Nel **Project** menu, fare clic su **Aggiungi riferimento al servizio**.  
  
2.  Nel **Aggiungi riferimento al servizio** finestra di dialogo, fare clic su **avanzate**.  
  
3.  Nel **Impostazioni riferimento al servizio** finestra di dialogo, fare clic su **Aggiungi riferimento Web**.  
  
4.  Nel **URL** finestra di **Aggiungi riferimento Web** della finestra di dialogo digitare l'URL per ottenere la descrizione del servizio Web ReportServer, ad esempio http://localhost/reportserver/reportservice2010.asmx. Scegliere il **Vai** pulsante per recuperare le informazioni sul servizio Web.  
  
     \- - oppure -  
  
     Se il servizio Web ReportServer presente nel computer locale, selezionare la **servizi Web sul computer locale** collegamento nel riquadro di esplorazione. quindi fare clic sul collegamento del servizio Web ReportService2010 nell'elenco visualizzato.  
  
5.  Nel **nome riferimento Web** casella, rinominare il riferimento Web in ReportService2010, ovvero lo spazio dei nomi si userà per questo riferimento Web.  
  
6.  Fare clic su **Aggiungi riferimento** per aggiungere un riferimento Web al servizio Web di destinazione.  
  
     Tramite [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verrà scaricata la descrizione del servizio e verrà generata una classe proxy che funge da interfaccia tra l'applicazione e il servizio Web ReportServer. È inoltre necessario aggiungere un riferimento allo spazio dei nomi <xref:System.Web.Services> per il riferimento Web da utilizzare.  
  
7.  Nel menu progetto, fare clic su **Aggiungi riferimento**.  
  
8.  Nel **Aggiungi riferimento** nella finestra di dialogo il **.NET** scheda, seleziona **System**, quindi fare clic su **OK**.  
  
 Per altre informazioni, vedere [Accesso all'API SOAP](../reporting-services/report-server-web-service/accessing-the-soap-api.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio Web ReportServer](../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Lezione 3: Accesso al servizio Web](../../2014/tutorials/lesson-3-accessing-the-web-service.md)   
 [L'accesso al servizio Web ReportServer con Visual Basic o Visual C#&#35; &#40;esercitazione su SSRS&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
