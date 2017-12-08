---
title: Impossibile caricare il file o assembly Microsoft ODS | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: power-pivot-sharepoint
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 175e7b5645a022dd7c840ae3065b4569bdf7a10f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="could-not-load-file-or-assembly-microsoft-data-services"></a>Impossibile caricare il file o assembly di servizi di dati Microsoft
  Negli ambienti SharePoint 2010 in cui è disponibile [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint questo errore si verifica se si prova un'esportazione del feed di dati e nel sistema non è installata la versione richiesta di Microsoft ADO.NET Data Services.  
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Applicabile a|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint|  
|Versione prodotto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|Impossibile trovare ADO.NET Data Services 3.5 SP1.|  
|Testo del messaggio|Impossibile caricare il file o l'assembly "Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral PublicKeyToken=b77a5c561934e089" o una delle relative dipendenze. Impossibile trovare il file specificato|  
  
## <a name="explanation"></a>Spiegazione  
 In SharePoint 2010 è incluso un pulsante Esporta come feed di dati che può essere utilizzato per esportare un elenco SharePoint come feed di dati XML. Inoltre, sia Reporting Services in modalità SharePoint sia [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint supportano le funzionalità dei feed di dati che richiedono ADO.NET Data Services.  
  
 Se ADO.NET Data Services non è installato, questo errore si verificherà quando si richiede un feed di dati.  
  
## <a name="user-action"></a>Azione dell'utente  
  
1.  Andare alla documentazione relativa alla modalità per [determinare i requisiti hardware e software per SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=169734) (http://go.microsoft.com/fwlink/?LinkId=169734).  
  
2.  Nella sezione relativa ai **prerequisiti software di installazione**cercare il collegamento per ADO.NET Data Services 3.5 che corrisponde al sistema operativo in uso.  
  
3.  Fare clic sul collegamento ed eseguire il programma di installazione che consente di installare il servizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuire soluzioni PowerPivot in SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
