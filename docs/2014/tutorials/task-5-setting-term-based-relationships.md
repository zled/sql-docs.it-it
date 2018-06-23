---
title: 'Attività 5: Impostazione basate su termini relazioni | Documenti Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b8450d3e77de578810bb57c35aafad6f90c8f19c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054109"
---
# <a name="task-5-setting-term-based-relationships"></a>Attività 5: Impostazione delle relazioni basate su termini
  In questa attività, è possibile definire alcune relazioni basate su termini per i valori per il **Supplier Name** dominio. Una relazione basata su termini consente di effettuare una correzione a un termine che fa parte di un valore in un dominio, consentendo in questo modo a più valori identici ad eccezione dell'ortografia di una parte in comune tra essi di essere considerati sinonimi identici. Ad esempio **Inc** possono essere corretti per **Incorporated**. Queste relazioni vengono utilizzate da DQS nei processi di individuazione delle informazioni, di pulizia o di corrispondenza. Vedere [relazioni basate su termini creare](http://msdn.microsoft.com/library/hh510404.aspx) per altri dettagli.  
  
1.  Selezionare **Supplier Name** nel **elenco domini**.  
  
2.  Passare il **relazioni basate su termini** scheda nel riquadro di destra.  
  
3.  Fare clic su **Aggiungi nuova relazione** pulsante sulla barra degli strumenti per aggiungere una relazione alla tabella.  
  
4.  Tipo di **co** per il **valore** campo e **aziendale** per il **Correggi in** campo.  
  
5.  Ripetere i due passaggi precedenti per i valori seguenti:  
  
    |valore|Correggi in|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![Relazioni basate su termini](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "relazioni basate su termini")  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 6: Impostazione di sinonimi](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  