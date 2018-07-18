---
title: Editor trasformazione ricerca (pagina colonne) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.columns.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: 690ffef5-fd59-4e95-a27d-4fcf0d6b1c0b
caps.latest.revision: 38
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 118d3a51afe868f1fa6449290a820e9b1b479867
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37199631"
---
# <a name="lookup-transformation-editor-columns-page"></a>Editor trasformazione Ricerca (pagina Colonne)
  Utilizzare la pagina **Colonne** della finestra di dialogo **Editor trasformazione Ricerca** per specificare il join tra la tabella di origine e la tabella di riferimento e selezionare colonne di ricerca nella tabella di riferimento.  
  
 Per ulteriori informazioni sulla trasformazione Ricerca, vedere [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Colonne di input disponibili**  
 Consente di visualizzare l'elenco delle colonne di input disponibili. Le colonne di input sono le colonne nel flusso di dati provenienti da un'origine connessa. Le colonne di input e le colonne di ricerca devono contenere tipi di dati corrispondenti.  
  
 Effettuare un'operazione di trascinamento della selezione per eseguire il mapping delle colonne di input disponibili alle colonne di ricerca.  
  
 È anche possibile eseguire il mapping delle colonne di input alle colonne di ricerca mediante la tastiera, evidenziando una colonna nella tabella **Colonne di input disponibili** , premendo il tasto MENU SCELTA RAPIDA, quindi facendo clic su **Modifica mapping**.  
  
 **Colonne di ricerca disponibili**  
 Consente di visualizzare l'elenco delle colonne di ricerca. Le colonne di ricerca sono colonne nella tabella di riferimento nelle quali si desidera cercare i valori corrispondenti alle colonne di input.  
  
 Eseguire un'operazione di trascinamento della selezione per eseguire il mapping delle colonne di ricerca disponibili alle colonne di input.  
  
 Utilizzare le caselle di controllo per selezionare le colonne di ricerca nella tabella di riferimento su cui eseguire operazioni di ricerca.  
  
 È anche possibile eseguire il mapping delle colonne di ricerca alle colonne di input mediante la tastiera, evidenziando una colonna nella tabella **Colonne di ricerca disponibili** , premendo il tasto MENU SCELTA RAPIDA, quindi facendo clic su **Modifica mapping**.  
  
 **Colonna di ricerca**  
 Consente di visualizzare le colonne di ricerca selezionate. Le selezioni effettuate vengono riflesse nelle selezioni delle caselle di controllo nella tabella **Colonne di ricerca disponibili** .  
  
 **Operazione di ricerca**  
 Consente di selezionare un'operazione di ricerca da eseguire sulla colonna di ricerca.  
  
 **Alias di output**  
 Consente di digitare un alias per l'output relativo a ogni colonna di ricerca. Per impostazione predefinita viene suggerito il nome della colonna di ricerca. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor trasformazione ricerca &#40;pagina Generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor trasformazione ricerca &#40;pagina di connessione&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [Editor trasformazione ricerca &#40;pagina avanzate&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [Editor trasformazione ricerca &#40;pagina dell'Output degli errori&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [Trasformazione Ricerca fuzzy](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
