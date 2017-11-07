---
title: Trusted percorso non consente le connessioni dati esterne | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: dc0cedfd-a7d0-40ef-bdd6-ea508130640a
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0f774f6bc9a4d950d8f7c00e3c3e79aa3211e4cf
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="trusted-location-does-not-allow-external-data-connections"></a>Percorso attendibile non consente le connessioni dati esterne
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
  
  

