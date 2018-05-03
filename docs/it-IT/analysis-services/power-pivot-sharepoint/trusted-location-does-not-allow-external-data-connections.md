---
title: Trusted percorso non consente le connessioni dati esterne | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ppvt-sharepoint
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 415399f067e353039e8dcf8300a84821791b03ca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="trusted-location-does-not-allow-external-data-connections"></a>Percorso attendibile non consente le connessioni dati esterne
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Per le cartelle di lavoro di Excel contenenti dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , Excel Services restituisce questo errore se non riesce a connettersi a origini dati incorporate.  
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Applicabile a|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint|  
|Versione prodotto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|Excel Services è configurato per negare l'accesso ai dati esterni.|  
|Testo del messaggio|Il percorso attendibile in cui è archiviata la cartella di lavoro non consente connessioni dati esterne. Impossibile aggiornare le connessioni seguenti: Dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
  
## <a name="explanation"></a>Spiegazione  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Le cartelle di lavoro contengono connessioni dati incorporate. Per supportare l'interazione della cartella di lavoro tramite filtri dei dati e filtri, Excel Services deve essere configurato in modo da consentire l'accesso ai dati esterni tramite informazioni di connessione incorporate. L'accesso ai dati esterni è necessario per il recupero di dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] caricati nei server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm.  
  
## <a name="user-action"></a>Azione dell'utente  
 Modificare le impostazioni di configurazione per consentire le origini dati incorporate.  
  
1.  In Gestione applicazioni di Amministrazione centrale fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Fare clic su **Applicazione Excel Services**.  
  
3.  Fare clic su **Posizione attendibile file**.  
  
4.  Fare clic su **http://** o sul percorso che si vuole configurare.  
  
5.  In Dati esterni di Impostazione dati esterni consentiti fare clic su **Raccolte di connessioni dati attendibili e connessioni incorporate**.  
  
6.  Scegliere **OK**.  
  
 In alternativa, è possibile creare un nuovo percorso attendibile per i siti che contengono cartelle di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] e quindi modificare le impostazioni di configurazione solo per questo sito. Per altre informazioni, vedere [Creare un percorso attendibile per i siti PowerPivot in Amministrazione centrale](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
