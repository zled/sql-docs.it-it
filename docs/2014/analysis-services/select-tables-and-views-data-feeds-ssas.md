---
title: Selezione tabelle e viste (feed di dati) (SSAS) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviewsdf.f1
ms.assetid: 6c4fafe0-e02e-47d1-b8bc-e70e872690af
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 199e225e6a3a4b63c704606418fae021b1ba3e9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157607"
---
# <a name="select-tables-and-views-data-feeds-ssas"></a>Selezione tabelle e viste (Feed di dati) (SSAS)
  Questa pagina dell'**Importazione guidata tabella** consente di selezionare le tabelle e le viste da cui importare dati. Per accedere alla procedura guidata da [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dal menu **Modello** selezionare **Importa da origine dati**.  
  
 L'aspetto delle tabelle e delle viste in questa pagina non garantisce che l'importazione verrà completata. Se l'utente specificato nella pagina Impostazioni di rappresentazione non dispone di privilegi sufficienti per leggere dal database selezionato, l'importazione non verrà completata.  
  
 Per origini dati in cui viene utilizzata l'autenticazione di Windows, le credenziali dell'utente corrente vengono utilizzate per recuperare le tabelle e le viste nella finestra di dialogo Selezione tabelle e viste. Per altre origini dati, vengono utilizzate le credenziali fornite nella stringa di connessione per il recupero dei dati.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **URL del feed di dati**  
 Viene visualizzato l'URL per il feed di dati selezionato.  
  
 **Tabelle e viste**  
 Elenca le tabelle e le viste nel feed di dati. Selezionare la casella di controllo accanto a ciascuna tabella e visualizzare la tabella che si desidera importare.  
  
 **Tabella di origine**  
 Specifica il nome della tabella di origine in base al tipo di origine dati.  
  
 **Nome descrittivo**  
 Specifica il nome descrittivo della tabella di origine. Per impostazione predefinita, nella colonna viene visualizzato il nome della tabella di origine presente nella colonna **Tabella di origine** .  
  
 **Dettagli filtro**  
 Visualizza il filtro per l'importazione dei dati nella finestra di dialogo **Dettagli filtro**, se è stato applicato un filtro ai dati importati. Per altre informazioni, vedere [Dettagli filtro &#40;DAX&#41;](filter-details-ssas.md).  
  
 **Anteprima e filtro**  
 Visualizza la finestra di dialogo **Anteprima tabella selezionata** usata per applicare un filtro ai dati importati. Per altre informazioni, vedere [Anteprima tabella selezionata &#40;SSAS&#41;](preview-selected-table-ssas.md).  
  
 **Selezione tabelle correlate**  
 Consente di selezionare le tabelle correlate alle tabelle e alle viste specificate dall'utente.  
  
  