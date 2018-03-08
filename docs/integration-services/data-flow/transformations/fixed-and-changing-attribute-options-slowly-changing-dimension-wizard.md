---
title: Opzioni attributi fissi e modificabili (Configurazione guidata dimensioni a modifica lenta) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff9390dbf0831673d7eca28e896a2ca2c61ead6a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a>Opzioni attributi fissi e modificabili (Configurazione guidata dimensioni a modifica lenta)
  Utilizzare la finestra di dialogo **Opzioni attributi fissi e modificabili** per specificare le modalità di risposta alle modifiche degli attributi fissi e modificabili.  
  
 Per ulteriori informazioni su questa procedura guidata, vedere [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Attributi fissi**  
 Per gli attributi fissi, consente di indicare se l'attività deve essere interrotta in caso venga rilevata una modifica a un attributo fisso.  
  
 **Attributi modificabili**  
 Per gli attributi modificabili, consente di indicare se l'attività deve modificare i record obsoleti o scaduti oltre ai record correnti, in caso venga rilevata una modifica a un attributo modificabile. Per record scaduto si intende un record che è stato sostituito con un record più recente mediante una modifica in un attributo cronologico (una modifica di tipo 2). Se si seleziona questa opzione, è possibile che vengano imposti ulteriori requisiti di elaborazione in un oggetto multidimensionale costruito sul data warehouse relazionale.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione degli output tramite Configurazione guidata dimensioni a modifica lenta](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
