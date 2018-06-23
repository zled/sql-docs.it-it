---
title: Le informazioni sulla rappresentazione | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42319d60-ccd0-46b8-af0b-f0968c390d8a
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 90a9d2102df9bd1b6cdf2bf1e4c7b3386c0fa825
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063504"
---
# <a name="impersonation-information"></a>Impostazioni di rappresentazione
  Usare la pagina **Impostazioni di rappresentazione** per specificare le credenziali usate da Analysis Services per la connessione all'origine dati.  
  
## <a name="options"></a>Opzioni  
 **Utilizzare un nome utente di Windows specifico e una password**  
 Selezionare questa opzione per fare in modo che l'oggetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] usi le credenziali di sicurezza di un account utente di Windows specificato. Le credenziali specificate verranno usate per l'elaborazione, le query ROLAP, le associazioni out-of-line, i cubi locali, i modelli di data mining, le partizioni remote, gli oggetti collegati e la sincronizzazione dalla destinazione all’origine. Per le istruzioni DMX (Data Mining Extensions) OPENQUERY, invece, questa opzione viene ignorata e verranno usate le credenziali dell'utente corrente.  
  
 **Nome utente**  
 Digitare il dominio e il nome dell'account utente che verranno usati dall'oggetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] selezionato. Utilizzare il formato seguente:  
  
 *\<Nome di dominio >* **\\**  *\<nome dell'account utente >*  
  
 Questa opzione è abilitata solo se si seleziona l'opzione **Usa nome utente e password specifici** .  
  
 **Password**  
 Digitare la password dell'account utente che verrà utilizzata dall'oggetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] selezionato.  
  
 Questa opzione è abilitata solo se si seleziona l'opzione **Usa nome utente e password specifici** .  
  
 **Usa account del servizio**  
 Selezionare questa opzione per fare in modo che l'oggetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilizzi le credenziali di sicurezza associate al servizio di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] che gestisce l'oggetto. Le credenziali dell'account del servizio verranno utilizzate per l'elaborazione, le query ROLAP, le partizioni remote, gli oggetti collegati e la sincronizzazione da un'origine a una destinazione. Per le istruzioni DMX (Data Mining Extensions) OPENQUERY, i cubi locali, i modelli di data mining, verranno utilizzate invece le credenziali dell'utente corrente. Questa opzione non è supportata per le associazioni out-of-line.  
  
 **Usa credenziali dell'utente corrente**  
 Selezionare questa opzione per fare in modo che l'oggetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilizzi le credenziali di sicurezza dell'utente corrente per le associazioni out-of-line, le istruzioni DMX OPENQUERY, i cubi locali e i modelli di data mining. Questa opzione non è supportata per l'elaborazione, le query ROLAP, le partizioni remote, gli oggetti collegati e la sincronizzazione da un'origine a una destinazione.  
  
 **Ereditare**  
 Selezionare questa opzione per utilizzare il comportamento della rappresentazione, definito al livello del database impostato dall'amministratore del server utilizzando la proprietà del database `DataSourceImpersonation`.  
  
## <a name="see-also"></a>Vedere anche  
 [Origini dati nei modelli multidimensionali](multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Origini dati supportate &#40;multidimensionale di SSAS&#41;](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  