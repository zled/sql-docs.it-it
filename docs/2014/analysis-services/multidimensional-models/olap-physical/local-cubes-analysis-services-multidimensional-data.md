---
title: I cubi locali (Analysis Services - dati multidimensionali) | Documenti Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], local
ms.assetid: e52e1515-35a7-4dc3-9bbf-736d176ba0c7
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bfb1b14d4dc540f13a98314d8cf299b78adf1550
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069492"
---
# <a name="local-cubes-analysis-services---multidimensional-data"></a>Cubi locali (Analysis Services - Dati multidimensionali)
  Per creare, aggiornare o eliminare cubi locali, è necessario scrivere ed eseguire uno script ASSL o un programma AMO.  
  
 I cubi locali e i modelli di data mining locali consentono di eseguire analisi in una workstation client disconnessa dalla rete. Un'applicazione client può ad esempio chiamare il provider OLE DB per OLAP 9.0 (MSOLAP.3), il quale carica il motore dei cubi locali per creare cubi locali ed eseguire query su di essi, come illustrato nella figura seguente:  
  
 ![Architettura client per i modelli e cubi locali](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "architettura Client per i modelli e cubi locali")  
  
 Il motore dei cubi locali viene inoltre caricato da ADMOD.NET e dalla libreria AMO (Analysis Management Objects) durante l'interazione con cubi locali. A un file di cubo locale può accedere un unico processo, poiché il motore dei cubi locali blocca un file di cubo locale in modo esclusivo quando stabilisce una connessione con esso. Durante uno stesso processo, sono consentite fino a cinque connessioni simultanee.  
  
 Un file con estensione cub può contenere più cubi o modelli di data mining. Le query eseguite su modelli di data mining e cubi locali vengono gestite dal motore dei cubi locali e non necessitano di una connessione a un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  L'utilizzo di [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] per la gestione di cubi locali non è supportato.  
  
## <a name="local-cubes"></a>Cubi locali  
 Un cubo locale può essere creato e popolato da un cubo esistente in un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza o da un'origine dati relazionale.  
  
|Origine dei dati per il cubo locale|Metodo di creazione|  
|------------------------------------|---------------------|  
|Cubo basato su server|È possibile utilizzare l'istruzione CREATE GLOBAL CUBE o un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] script Scripting Language (ASSL) per creare e popolare un cubo da un cubo basato su server. Per altre informazioni, vedere [CREATE GLOBAL CUBE-istruzione &#40;MDX&#41; ](/sql/mdx/mdx-data-definition-create-global-cube) o [Analysis Services Scripting Language &#40;ASSL&#41; riferimento](../../scripting/analysis-services-scripting-language-assl-for-xmla.md).|  
|Origine dei dati relazionale|Per creare e popolare un cubo da un database relazionale OLE DB è possibile utilizzare uno script ASSL. Per creare un cubo locale tramite ASSL, è sufficiente connettersi a un file di cubo locale con estensione cub ed eseguire lo script ASSL così come in caso di esecuzione di uno script ASSL su un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per creare un cubo sul server. Per altre informazioni, vedere [Analysis Services Scripting Language &#40;ASSL&#41; riferimento](../../scripting/analysis-services-scripting-language-assl-for-xmla.md).|  
  
 Utilizzare l'istruzione REFRESH CUBE per ricompilare un cubo locale e aggiornarne i dati. Per altre informazioni, vedere [REFRESH CUBE-istruzione &#40;MDX&#41;](/sql/mdx/mdx-data-definition-refresh-cube).  
  
### <a name="local-cubes-created-from-server-based-cubes"></a>Cubi locali creati da cubi basati su server  
 In caso di creazione di cubi locali a partire da cubi basati su server, si applicano le considerazioni seguenti:  
  
-   Non sono supportate misure Distinct Count.  
  
-   Quando si aggiunge una misura, è inoltre necessario includere almeno una dimensione correlata alla misura aggiunta. Per ulteriori informazioni sulle relazioni tra dimensioni a gruppi di misure, vedere [relazioni tra dimensioni](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
-   Quando si aggiunge una gerarchia padre-figlio, i relativi livelli e filtri vengono ignorati e viene inclusa l'intera gerarchia padre-figlio.  
  
-   Non vengono create proprietà dei membri.  
  
-   Quando si include una misura semiadditiva, non sono consentite sezioni nella dimensione di tipo Conti o temporale.  
  
-   Le dimensioni di riferimento vengono sempre materializzate.  
  
-   Se si include una dimensione molti-a-molti, è necessario rispettare le regole seguenti:  
  
    -   Non è possibile sezionare la dimensione molti-a-molti.  
  
    -   È necessario aggiungere una misura dal gruppo di misure intermedio.  
  
    -   Non è possibile sezionare dimensioni comuni ai due gruppi di misure coinvolti nella relazione molti-a-molti.  
  
-   Nel cubo locale verranno inclusi soltanto i membri calcolati, i set denominati e le assegnazioni basati su misure e dimensioni aggiunte al cubo locale. I membri calcolati, i set denominati e le assegnazioni non validi verranno automaticamente esclusi.  
  
### <a name="security"></a>Security  
 Affinché un utente di creare un cubo locale da un cubo sul server, l'utente deve essere concessa **drill-through e cubo locale** le autorizzazioni per il cubo sul server. Per altre informazioni, vedere [concedere le autorizzazioni del cubo o modello &#40;Analysis Services&#41;](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).  
  
 I cubi locali non sono protetti tramite ruoli come i cubi sul server. Qualsiasi utente con accesso a livello di file per un file di cubo locale può eseguire query sui cubi in esso contenuti. È possibile utilizzare la proprietà di connessione `Encryption Password` in un cubo locale per impostare una password per un file di cubo locale. Con l'impostazione di una password per un file di cubo locale, tutte le successive connessioni a tale file dovranno utilizzare la password per eseguire query sul file.  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione CREATE GLOBAL CUBE &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)   
 [Sviluppo con Analysis Services Scripting Language &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Istruzione di aggiornamento cubo &#40;MDX&#41;](/sql/mdx/mdx-data-definition-refresh-cube)  
  
  
