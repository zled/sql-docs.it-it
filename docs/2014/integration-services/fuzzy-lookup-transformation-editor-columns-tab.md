---
title: Editor trasformazione Ricerca fuzzy (scheda colonne) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.columns.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2486303ca887e26f0583457bd3571c937f089144
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062224"
---
# <a name="fuzzy-lookup-transformation-editor-columns-tab"></a>Editor trasformazione Ricerca fuzzy (scheda Colonne)
  Utilizzare la scheda **Colonne** della finestra di dialogo **Editor trasformazione Ricerca fuzzy** per impostare le proprietà delle colonne di input e output.  
  
 Per ulteriori informazioni sulla trasformazione Ricerca fuzzy, vedere [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Colonne di input disponibili**  
 Trascinare le colonne di input per collegarle alle colonne di ricerca disponibili. Queste colonne devono disporre di tipi di dati supportati e corrispondenti. Selezionare una riga di mapping e fare clic con il pulsante destro del mouse per modificare i mapping nella finestra di dialogo [Crea relazioni](data-flow/transformations/create-relationships.md) .  
  
 **Nome**  
 Consente di visualizzare i nomi delle colonne di input disponibili.  
  
 **Pass-through**  
 Consente di indicare l'inclusione delle colonne di input nell'output della trasformazione.  
  
 **Colonne di ricerca disponibili**  
 Utilizzare le caselle di controllo per selezionare le colonne su cui eseguire operazioni di ricerca fuzzy.  
  
 **Colonna di ricerca**  
 Selezionare le colonne di ricerca dall'elenco delle colonne della tabella di riferimento disponibili. Queste selezioni si rifletteranno nelle selezioni delle caselle di controllo nella tabella **Colonne di ricerca disponibili** . La selezione di una colonna nella tabella **Colonne di ricerca disponibili** comporta la creazione di una colonna di output contenente il valore della colonna della tabella di riferimento per ogni riga corrispondente restituita.  
  
 **Alias di output**  
 Consente di digitare un alias per l'output relativo a ogni colonna di ricerca. Per impostazione predefinita viene suggerito il nome della colonna di ricerca a cui è accodato un valore di indice numerico. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per i messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione Ricerca fuzzy &#40;scheda tabella di riferimento&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Editor trasformazione Ricerca fuzzy &#40;scheda Avanzate&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  