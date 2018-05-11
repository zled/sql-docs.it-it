---
title: Proprietà tabella | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7cfe22cf11a49b7597e665221b272078213470be
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="table-properties"></a>Table Properties 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  In questo articolo vengono descritte le proprietà di tabella di modello tabulare. Le proprietà descritte differiscono da quelle presenti nella finestra di dialogo Modifica proprietà tabella, che consentono di definire quali colonne vengono importate dall'origine.  
  
 Sezioni dell'argomento:  
  
-   [Table Properties](#bkmk_properties)  
  
-   [Configurare le impostazioni delle proprietà delle tabelle](#bkmk_config_prop)  
  
##  <a name="bkmk_properties"></a> Table Properties  
 **Basic**  
  
|Proprietà|Impostazione predefinita|Description|  
|--------------|---------------------|-----------------|  
|**Nome connessione**|\<nome della connessione >|Nome della connessione all'origine dati della tabella.<br /><br /> Per modificare la connessione, fare clic sul pulsante.|  
|**Hidden**|False|Viene specificato se la tabella è nascosta dalla visualizzazione negli elenchi dei campi del client di creazione report.|  
|**Partizioni**||Le partizioni per la tabella non possono essere visualizzate nella finestra **Proprietà** . Per visualizzare, creare o modificare partizioni, fare clic sul pulsante per aprire Gestione partizioni.|  
|**Origine dati**||I dati di origine per la tabella non possono essere visualizzati nella finestra **Proprietà** . Per visualizzare o modificare i dati di origine, fare clic sul pulsante per aprire la finestra di dialogo Modifica proprietà tabella.|  
|**Descrizione tabella**||Descrizione di testo per la tabella.<br /><br /> In [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], se un utente finale posiziona il cursore su questa tabella nell'elenco dei campi, la descrizione viene visualizzata come descrizione comando.|  
|**Nome tabella**|\<nome descrittivo >|Viene specificato il nome descrittivo della tabella. È possibile specificare il nome di tabella quando una tabella viene importata utilizzando l'Importazione guidata tabella oppure in qualsiasi momento dopo l'importazione. Il nome della tabella nel modello può essere diverso dalla tabella associata nell'origine. Il nome descrittivo della tabella viene visualizzato nell'elenco di campi dell'applicazione client di creazione report, nonché nel database modello in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
  
 **Proprietà report**  
  
 Per descrizioni dettagliate e informazioni di configurazione per le proprietà dei report, vedere [proprietà report Power View](../../analysis-services/tabular-models/power-view-reporting-properties-ssas-tabular.md).  
  
|Proprietà|Impostazione predefinita|Description|  
|--------------|---------------------|-----------------|  
|**Set di campi predefiniti**|||  
|Comportamento tabella|||  
  
##  <a name="bkmk_config_prop"></a> Configurare le impostazioni delle proprietà delle tabelle  
  
1.  In Progettazione modelli, in Vista dati fare clic su una tabella (scheda) oppure in Vista diagramma fare clic su un'intestazione di tabella.  
  
2.  Nella finestra **Proprietà** fare clic su una proprietà, quindi digitare un valore oppure fare clic sul pulsante per ulteriori opzioni di configurazione.  
  
  
