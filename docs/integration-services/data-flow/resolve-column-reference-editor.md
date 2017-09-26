---
title: Editor della risoluzione colonne riferimento | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.resolvereferences.preview.F1
- sql13.dts.designer.resolvereferences.mapper.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f2ff8a97d45d75c3e93d4aa3111b653c9612b889
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="resolve-column-reference-editor"></a>Editor della risoluzione dei riferimenti alle colonne
  Quando un percorso di input viene disconnesso o se contiene colonne senza mapping, viene visualizzata un'icona di errore accanto al percorso di dati corrispondente. Per semplificare la risoluzione di errori di riferimento di colonna, l'editor di risoluzione dei riferimenti consente di collegare le colonne di output con colonne di input senza mapping per tutti i percorsi nell'albero di esecuzione. Nell'editor per la risoluzioni dei riferimenti verranno inoltre evidenziati i percorsi risolti.  
  
> [!NOTE]  
>  È possibile modificare un componente quando il relativo percorso di input è disconnesso  
  
 Dopo che sono stati risolti tutti i riferimenti alle colonne, in assenza di altri errori del percorso dati, accanto al percorso dati non verranno più visualizzate altre icone di errore.  
  
## <a name="options"></a>Opzioni  
 **Colonne di Output senza mapping (origine)**    
 Colonne del percorso a monte di cui non è stato eseguito il mapping  
  
**Colonne con mapping (origine)**    
 Colonne del percorso a monte di cui è stato eseguito il mapping alle colonne del percorso a valle  
  
**Colonne con mapping (destinazione)**    
 Colonne del percorso a monte di cui è stato eseguito il mapping alle colonne del percorso a valle  
  
**Colonne di Input senza mapping (destinazione)**    
 Colonne del percorso a valle di cui non è stato eseguito il mapping  
  
**Elimina colonne input senza mapping**  
 Selezionare Elimina colonne input senza mapping per ignorare le colonne senza mapping alla destinazione del percorso dati. Il pulsante Anteprima modifiche consente di visualizzare un elenco delle modifiche che si verificheranno alla pressione del pulsante OK.  
  
  
