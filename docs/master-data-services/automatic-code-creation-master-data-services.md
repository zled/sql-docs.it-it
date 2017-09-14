---
title: Creazione di codice automatica (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
caps.latest.revision: 8
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 9eba993695071796b6f9a4dfb4b05a1d1382be5a
ms.contentlocale: it-it
ms.lasthandoff: 09/07/2017

---
# <a name="automatic-code-creation-master-data-services"></a>Creazione di codice automatica (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]è possibile generare automaticamente valori numerici per l'attributo Code o per qualsiasi altro attributo numerico. Quando i codici vengono generati automaticamente, è possibile immettere altri valori per i codici anche se un valore iniziale viene impostato automaticamente.  
  
## <a name="generating-code-values"></a>Generazione di valori per l'attributo Code  
 Gli amministratori possono configurare valori generati automaticamente per l'attributo Code modificando le proprietà dell'entità associata. Possono specificare un valore iniziale e ogni valore successivo viene incrementato di uno.  
  
 Quando si caricano i valori Code in MDS in uno degli strumenti o utilizzando il processo di gestione temporanea, è possibile lasciare vuoto il valore Code perché ne verrà generato uno automaticamente. In alternativa, è possibile specificare un valore Code a scelta.  
  
## <a name="generating-other-attribute-values"></a>Generazione di altri valori di attributo  
 Gli amministratori possono generare automaticamente valori per attributi diversi da Code creando regole business. Possono specificare un valore iniziale e il numero per l'incremento di ogni valore successivo.  
  
 Quando si immettono i valori di attributo in MDS in uno degli strumenti o utilizzando il processo di gestione temporanea, è possibile lasciare vuoto il valore dell'attributo. Quando vengono applicate le regole business, i valori verranno incrementati in base al valore esistente più elevato. Ad esempio, se la regola è "Attributo predefinito a un valore generato che inizia da 1 e aumenta di 4" e il valore corrente più elevato per l'attributo è 700, il valore per il membro successivo aggiunto sarà 704.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Generare automaticamente valori per l'attributo Code.|[Generare automaticamente valori per l'attributo Code &#40;Master Data Services&#41;](../master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|Generare automaticamente valori per altri attributi.|[Generare automaticamente valori di attributi diversi da Code &#40;Master Data Services&#41;](../master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Panoramica di Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Regole di business &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [Entità &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  
