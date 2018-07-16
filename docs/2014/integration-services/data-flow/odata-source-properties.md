---
title: Proprietà dell'origine OData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2962314147f86723870a38dfa8998b3a734a68f1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37307951"
---
# <a name="odata-source-properties"></a>Proprietà dell'origine OData
  Quando si fa clic con il pulsante destro del mouse su **Origine OData** nel flusso di dati e si sceglie **Proprietà**, vengono visualizzate le proprietà per il componente **Origine OData** nella finestra **Proprietà**.  
  
|||  
|-|-|  
|Proprietà|Description|  
|CollectionName|Nome della raccolta che si desidera recuperare dal servizio OData. La proprietà **CollectionName** viene utilizzata quando **UseResourcePath** è False.<br /><br /> Questa proprietà ammette le espressioni e consente l'impostazione del valore in fase di esecuzione. Tuttavia, se i metadati della raccolta non corrispondono a quelli utilizzati in fase di progettazione, si verifica un errore di convalida e l'esecuzione del flusso di dati non viene completata.|  
|DefaultStringLength|Con questo valore viene specificata la lunghezza predefinita per le colonne stringa che sono prive della lunghezza massima.<br /><br /> **Valore predefinito:** 4000|  
|Query|Parametri della query OData. Questa proprietà ammette le espressioni e può essere impostata in fase di esecuzione.|  
|ResourcePath|Utilizzare questa proprietà quando è necessario specificare un percorso completo della risorsa, anziché selezionare semplicemente il nome di una raccolta. Questa proprietà viene utilizzata quando **UseResourcePath** è True.|  
|UseResourcePath|Quando impostato su True, il valore di **ResourcePath** viene aggiunto all'URL di base per determinare il percorso del feed OData. Quando impostato su False, viene utilizzato il valore di **CollectionName** .<br /><br /> **Valore predefinito:** False|  
  
  
