---
title: Installare ADO.NET Data Services per supportare dati esportazioni di feed di elenchi SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: d4241d56aa3257bd0ec2cddf4b439a4939f8ab9f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065017"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>Installare ADO.NET Data Services per supportare esportazioni di feed di dati di elenchi SharePoint
  ADO.NET Data Services è necessario per un'esportazione dei feed di dati di elenchi SharePoint. SharePoint 2010 non include questo componente nel programma di installazione essenziale di SharePoint, pertanto è necessario installarlo manualmente.  
  
 Senza questo prerequisito, si otterrà l'errore seguente quando si tenta di utilizzare un elenco SharePoint esportato come feed di dati: "Per motivi di sicurezza, la dichiarazione DTD non è consentita in questo documento XML. Per abilitare l'elaborazione DTD impostare la proprietà ProhibitDtd in XmlReaderSettings su false e passare le impostazioni al metodo XmlReader.Create".  
  
 Utilizzare le istruzioni seguenti per installare ADO.NET Data Services in ogni server SharePoint per il quale si desidera l'esportazione degli elenchi come feed di dati.  
  
### <a name="download-and-install-adonet-data-services"></a>Scaricare e installare ADO.NET Data Services  
  
1.  Andare alla documentazione di requisiti hardware e software per SharePoint 2010, [requisiti Hardware e Software (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  In **accedere a software applicabile**, cercare il collegamento per ADO.NET Data Services 3.5 che corrisponde al sistema operativo è in uso (Windows Server 2008 SP2 o Windows Server 2008 R2).  
  
3.  Fare clic sul collegamento ed eseguire il programma di installazione che consente di installare il servizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione PowerPivot per SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  