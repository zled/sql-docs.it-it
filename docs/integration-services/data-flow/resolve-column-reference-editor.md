---
title: Editor della risoluzione dei riferimenti alle colonne | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.resolvereferences.preview.F1
- sql13.dts.designer.resolvereferences.mapper.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d2c95ca874fcb626343cda6df7e850040bc59fe4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="resolve-column-reference-editor"></a>Editor della risoluzione dei riferimenti alle colonne
  Quando un percorso di input viene disconnesso o se contiene colonne senza mapping, viene visualizzata un'icona di errore accanto al percorso di dati corrispondente. Per semplificare la risoluzione degli errori di riferimento alle colonne, l'editor per la risoluzione dei riferimenti consente di collegare le colonne di output senza mapping alle colonne di input senza mapping per tutti i percorsi nell'albero di esecuzione. Nell'editor per la risoluzioni dei riferimenti verranno inoltre evidenziati i percorsi risolti.  
  
> [!NOTE]  
>  È possibile modificare un componente anche quando il relativo percorso di input è disconnesso  
  
 Dopo che sono stati risolti tutti i riferimenti alle colonne, in assenza di altri errori del percorso dati, accanto al percorso dati non verranno più visualizzate altre icone di errore.  
  
## <a name="options"></a>Opzioni  
 **Colonne di output senza mapping (Origine)**    
 Colonne del percorso a monte di cui non è stato eseguito il mapping  
  
**Colonne con mapping (Origine)**    
 Colonne del percorso a monte di cui è stato eseguito il mapping alle colonne del percorso a valle  
  
**Colonne con mapping (Destinazione)**    
 Colonne del percorso a monte di cui è stato eseguito il mapping alle colonne del percorso a valle  
  
**Colonne di input senza mapping (Destinazione)**    
 Colonne del percorso a valle di cui non è stato eseguito il mapping  
  
**Elimina colonne input senza mapping**  
 Selezionare Elimina colonne input senza mapping per ignorare le colonne senza mapping alla destinazione del percorso dati. Il pulsante Anteprima modifiche consente di visualizzare un elenco delle modifiche che si verificheranno alla pressione del pulsante OK.  
  
  
