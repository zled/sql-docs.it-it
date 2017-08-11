---
title: Ricerca di report e altri elementi (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a586659-5c2b-453b-8f40-a3a469277b17
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9663bbf0c11ce1d41f02cc22027f2c69aa07b057
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="searching-for-reports-and-other-items-report-builder--and-ssrs"></a>Ricerca di report e altri elementi (Generatore report e SSRS)
  È possibile utilizzare Gestione report per cercare elementi specifici in un server di report utilizzando il nome o la descrizione degli elementi come criteri di ricerca. È possibile cercare report pubblicati, modelli di report, cartelle, origini dei dati condivise e risorse. Non è possibile cercare pianificazioni, proprietari, assegnazioni di ruolo, snapshot specifici della cronologia dei report o sottoscrizioni. La ricerca viene eseguita nel database del server di report in cui vengono archiviati gli elementi.  
  
> [!NOTE]  
>  Se si esegue una ricerca nel file system, nei risultati non saranno compresi elementi gestiti da un server di report.  
  
-   Per cercare elementi in Gestione report, digitare una stringa di ricerca nella casella di testo **Cerca** nella parte superiore della pagina. Le ricerche iniziano dal nodo principale della gerarchia di cartelle e proseguono in ogni ramo. Se non si dispone delle autorizzazioni per l'accesso a un ramo specifico, questo viene ignorato. Questa regola è valida per le cartelle Report personali appartenenti ad altri utenti e per altre cartelle che in genere non sono disponibili. Nei risultati delle ricerche sono inclusi solo i report e gli elementi che l'utente che esegue la ricerca è autorizzato a visualizzare.  
  
-   Per cercare un elemento in base al nome o alla descrizione, specificare tutto il testo per il quale si desidera trovare una corrispondenza o solo parte di esso. La stringa di ricerca non supporta la distinzione tra maiuscole e minuscole. Non è possibile utilizzare operatori di ricerca quali i segni di addizione (+) o di sottrazione (–) per includere o escludere i criteri di ricerca.  
  
-   Per cercare testo specifico all'interno di un report, utilizzare la barra degli strumenti nella parte superiore del report.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca e visualizzazione di report in Gestione Report &#40; Generatore report e SSRS &#41;](https://msdn.microsoft.com/library/dd255286.aspx)   
 [Utilizzando i report &#40; Generatore report e SSRS &#41;](../../reporting-services/report-builder/using-my-reports-report-builder-and-ssrs.md)   
 [La ricerca, visualizzazione e gestione di report &#40; Generatore report e SSRS &#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Apertura e chiusura di un Report &#40; Gestione report &#41;](../../reporting-services/reports/open-and-close-a-report-report-manager.md)  
  
  
