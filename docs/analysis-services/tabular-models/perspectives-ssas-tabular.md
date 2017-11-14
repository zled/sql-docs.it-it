---
title: Prospettive (SSAS tabulare) | Documenti Microsoft
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f78c3a1-ce2c-4e7f-a277-71a657692bea
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a9c1ad93e5c4af1736721436f4ce5116ac279934
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="perspectives"></a>Prospettive
  Nei modelli tabulari, le prospettive consentono di definire subset visualizzabili di un modello in grado di offrire punti di vista mirati, specifici di un'attività aziendale o di un'applicazione del modello.  
  
##  <a name="bkmk_understanding"></a> Vantaggi  
 L'esplorazione dei modelli tabulari può risultare molto complessa per gli utenti. Un singolo modello può rappresentare il contenuto di un data warehouse completo con molte tabelle, misure e dimensioni. Tale complessità può costituire un ostacolo per gli utenti che necessitano solo di interagire con una piccola parte del modello per soddisfare determinati requisiti di Business Intelligence e creazione di report.  
  
 In una prospettiva, tabelle, colonne e misure (indicatori KPI inclusi) vengono definiti come oggetti campo. È possibile selezionare i campi visualizzabili per ogni prospettiva. In un modello possono ad esempio essere contenuti dati del prodotto, delle vendite, finanziari, geografici e dei dipendenti. Mentre un reparto vendite necessita di dati del prodotto, delle vendite, delle promozioni e geografici, non avrà probabilmente bisogno dei dati dei dipendenti e finanziari. In modo analogo, per un reparto risorse umane non sono necessari dati geografici e sulle promozioni di vendita.  
  
 Se un utente si connette a un modello (come origine dati) con prospettive definite, potrà selezionare la prospettiva desiderata. Se ad esempio ci si connette a un'origine dati del modello di Excel, gli utenti del reparto risorse umane potranno selezionare la prospettiva Risorse umane nella pagina Selezione tabelle e viste della Connessione guidata dati. Nell'elenco di campi della tabella pivot verranno visualizzati solo i campi (tabelle, colonne e misure) definiti per la prospettiva Risorse umane.  
  
 Le prospettive non sono pensate per essere utilizzate come meccanismo di sicurezza, ma piuttosto come strumento per migliorare l'esperienza utente. Tutte le impostazioni di sicurezza di una determinata prospettiva vengono ereditate dal modello sottostante. Le prospettive non possono consentire l'accesso agli oggetti del modello se l'utente non dispone già del relativo diritto di accesso. È quindi necessario risolvere la sicurezza del database modello prima di poter fornire l'accesso agli oggetti del modello tramite una prospettiva. I ruoli di sicurezza possono essere utilizzati per proteggere i metadati e i dati del modello. Per ulteriori informazioni, vedere [ruoli](../../analysis-services/tabular-models/roles-ssas-tabular.md).  
  
##  <a name="bkmk_testpersp"></a> Testing perspectives  
 Quando si crea un modello, è possibile utilizzare la caratteristica Analizza in Excel in Progettazione modelli per eseguire un test circa l'efficacia delle prospettive definite. Se si fa clic su **Analizza in Excel** nel menu **Modello**in Progettazione modelli prima che venga aperto Excel, verrà visualizzata la finestra di dialogo **Scegli credenziali e prospettiva** . In questa finestra di dialogo è possibile specificare il nome utente corrente, un utente diverso, un ruolo e una prospettiva che verranno utilizzati per la connessione al database dell'area di lavoro modello come origine dati nonché per la visualizzazione dei dati.  
  
##  <a name="bkmk_related_tasks"></a> Related tasks  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Creare e gestire prospettive](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)|Viene descritto come creare e gestire prospettive utilizzando la finestra di dialogo Prospettive in Progettazione modelli.|  
  
## <a name="see-also"></a>Vedere anche  
 [Ruoli](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [Gerarchie](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)  
  
  

