---
title: "Questa cartella di lavoro contiene una o più query che aggiornano dati esterni | Documenti Microsoft"
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
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 882a0dca2f6c2c443507bc5b4d54820711e55ae7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a>Questa cartella di lavoro contiene una o più query che aggiornano dati esterni
  Per le cartelle di lavoro di Excel contenenti dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , Excel Services visualizza questo avviso quando vengono rilevate le informazioni di connessione e viene richiesto di abilitare o disabilitare le query per questa cartella di lavoro.  
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] per SharePoint|  
|Versione prodotto|[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11_md](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14_md](../../includes/sssql14-md.md)]|  
|Causa|Excel Services è configurato per avvisare in caso di aggiornamento dati.|  
|Testo del messaggio|La cartella di lavoro contiene una o più query che aggiornano dati esterni. Un utente malintenzionato potrebbe creare una query per accedere a informazioni riservate e distribuirle ad altri utenti o eseguire altre azioni dannose.<br /><br /> Se la cartella di lavoro proviene da una fonte attendibile, fare clic su Sì per consentire le query su dati esterni nella cartella di lavoro. In caso contrario, fare clic su No in modo che le modifiche non vengano applicate alla cartella di lavoro.<br /><br /> Consentire le query su dati esterni nella cartella di lavoro?|  
  
## <a name="explanation"></a>Spiegazione  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] le cartelle di lavoro contengono stringhe di connessione dati incorporate utilizzate da Excel per comunicare con un server [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] esterno che carica e calcola i dati. Quando l'avviso in caso di aggiornamento dati è abilitato, Excel Services rileva questa stringa di connessione e avvisa l'utente di conseguenza.  
  
 Per filtrare e sezionare i dati [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] nella cartella di lavoro, le query devono essere abilitate. Assicurarsi di abilitare le query solo per le cartelle di lavoro di [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] attendibili.  
  
## <a name="user-action"></a>Azione dell'utente  
 Fare clic su **Sì** per abilitare le query.  
  
 È anche possibile modificare le impostazioni di configurazione in modo da non ricevere più l'avviso in caso di aggiornamento:  
  
1.  In Gestione applicazioni di Amministrazione centrale fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Fare clic su **Applicazione Excel Services**.  
  
3.  Fare clic su **Posizione attendibile file**.  
  
4.  Fare clic su **http://** o sul percorso che si desidera configurare.  
  
5.  In Dati esterni deselezionare la casella di controllo per **Avvisa in caso di aggiornamento**.  
  
6.  Scegliere **OK**.  
  
 In alternativa, è possibile creare un nuovo percorso attendibile per i siti che contengono cartelle di lavoro di [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] e quindi modificare le impostazioni di configurazione solo per questo sito. Per altre informazioni, vedere [Creare un percorso attendibile per i siti PowerPivot in Amministrazione centrale](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
