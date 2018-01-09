---
title: Commenti (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: DMX
helpviewer_keywords:
- comments [DMX]
- Data Mining Extensions [Analysis Services], comments
- double forward slashes
- commenting characters
- text strings [SQL Server]
- remarks [DMX]
- forward slash-asterisk character pairs
- DMX [Analysis Services], comments
- /*...*/ (comment)
- double hyphens
- // (comment)
- -- (comment character)
ms.assetid: 64d10eb5-4fe8-42c6-b387-eff336315e56
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 86fd2ea716fd0366149937af749c240fe01e486d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="comments-dmx"></a>Commenti (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  I commenti in DMX Data Mining Extensions () sono stringhe di testo nel programma di codice che [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] non viene eseguito. I commenti sono noti anche come osservazioni. È possibile utilizzare i commenti per documentare il codice o disabilitare temporaneamente parti di uno script o di un'istruzione DMX durante la diagnostica del codice.  
  
 Se si utilizzano i commenti per documentare il codice del programma, la successiva manutenzione del codice risulterà più semplice. È possibile utilizzare i commenti per registrare dettagli quali il nome del programma, il nome dello sviluppatore che ha scritto il codice e le date delle principali modifiche apportate al codice. È inoltre possibile utilizzare i commenti per descrivere calcoli complessi o un metodo di programmazione.  
  
 Di seguito sono riportate le linee guida di base per la scrittura dei commenti:  
  
-   In un commento è possibile utilizzare caratteri alfanumerici o simboli. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ignora tutti i caratteri all'interno di un commento.  
  
-   Per i commenti di uno script o istruzione non è prevista una lunghezza massima. Un commento può essere formato da una o più righe.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supporta gli indicatori di commento seguenti:  
  
-   **(barra doppia).** Usare questi caratteri di commento per scrivere un commento nella stessa riga di codice da eseguire oppure per scrivere un commento in una riga distinta. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considera tutti i caratteri situati tra la barra doppia e la fine della riga come commento. Per creare commenti su più righe, specificare la barra doppia all'inizio di ogni riga di commento. Per ulteriori informazioni su questo indicatore di commento, vedere [barre doppie &#40; Commento &#41; &#40; DMX &#41; ](../dmx/double-slash-comment-dmx.md).  
  
-   **-(trattino doppio).** Usare questi caratteri di commento per scrivere un commento nella stessa riga di codice da eseguire oppure per scrivere un commento in una riga distinta. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considera tutti i caratteri situati tra il trattino doppio e la fine della riga come commento. Per creare commenti su più righe, specificare il trattino doppio all'inizio di ogni riga di commento. Per ulteriori informazioni su questo indicatore di commento, vedere [-&#40; Commento &#41; &#40; DMX &#41; Riepilogo](../dmx/comment-dmx-summary.md).  
  
-   **/\*... \*/ (barra-asterisco coppie di caratteri).** Usare questi caratteri di commento per scrivere un commento nella stessa riga di codice da eseguire oppure per scrivere un commento in una riga distinta, o anche per scrivere commenti in un codice eseguibile. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]i caratteri situati tra la coppia di commenti di apertura (/ *) per la coppia di chiusura del commento (\*/) come parte del commento. Per creare un commento su più righe, iniziare il commento con la coppia di caratteri di apertura del commento (/\*) e terminare il commento con la coppia di caratteri di chiusura del commento (\*/). Nelle righe del commento non deve essere inserito nessun altro simbolo di commento. Per ulteriori informazioni su questo indicatore di commento, vedere [barra stella &#40; Commento &#41; &#40; DMX &#41; ](../dmx/slash-star-comment-dmx.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40; DMX &#41; Convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40; DMX &#41; Elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
