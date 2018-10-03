---
title: "Il percorso della connessione dati nella cartella di lavoro fa riferimento a un file nell'unità locale o è un URI non valido. Impossibile aggiornare le connessioni seguenti: dati PowerPivot | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6242e258c8516b4ebd6e46e9290dabe31cbaf168
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164121"
---
# <a name="the-data-connection-path-in-the-workbook-points-to-a-file-on-the-local-drive-or-is-an-invalid-uri-the-following-connections-failed-to-refresh-powerpivot-data"></a>Il percorso della connessione dati nella cartella di lavoro fa riferimento a un file nell'unità locale o è un URI non valido. Impossibile aggiornare le connessioni seguenti: Dati PowerPivot
  Per cartelle di lavoro di Excel contenenti dati PowerPivot, in Excel Services viene restituito questo errore se non è possibile connettersi a origini dati incorporate.  
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Applicabile a|PowerPivot per SharePoint|  
|Versione prodotto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|Excel Services è configurato per consentire solo connessioni dati da file con estensione odc inclusi in una raccolta connessioni dati attendibili.|  
|Testo del messaggio|Il percorso della connessione dati nella cartella di lavoro fa riferimento a un file nell'unità locale o è un URI non valido. Impossibile aggiornare le connessioni seguenti: Dati PowerPivot|  
  
## <a name="explanation"></a>Spiegazione  
 Le cartelle di lavoro di PowerPivot contengono connessioni dati incorporate. Per supportare l'interazione della cartella di lavoro tramite filtri dei dati e filtri, Excel Services deve essere configurato in modo da consentire l'accesso ai dati esterni tramite informazioni di connessione incorporate. L'accesso ai dati esterni è necessario per il recupero di dati PowerPivot caricati sui server PowerPivot nella farm.  
  
## <a name="user-action"></a>Azione dell'utente  
 Modificare le impostazioni di configurazione per consentire le connessioni alle origini dati incorporate.  
  
1.  In Gestione applicazioni di Amministrazione centrale fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Fare clic su **Applicazione Excel Services**.  
  
3.  Fare clic su **Posizione attendibile file**.  
  
4.  Fare clic su **http://** o sul percorso che si vuole configurare.  
  
5.  In Dati esterni di Impostazione dati esterni consentiti fare clic su **Raccolte di connessioni dati attendibili e connessioni incorporate**.  
  
6.  Fare clic su **OK**.  
  
 In alternativa, è possibile creare un nuovo percorso attendibile per i siti che contengono cartelle di lavoro di PowerPivot, quindi modificare le impostazioni di configurazione solo per questo sito. Per altre informazioni, vedere [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
