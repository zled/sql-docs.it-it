---
title: Colonne dimensioni a modifica lenta (Configurazione guidata dimensioni a modifica lenta) | Microsoft Docs
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
f1_keywords: sql13.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
caps.latest.revision: "23"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5cdf56b8da5d4c952c2202264125a9a48461f3e6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a>Colonne dimensioni a modifica lenta (Configurazione guidata dimensioni a modifica lenta)
  Utilizzare la finestra di dialogo **Colonne dimensioni a modifica lenta** per selezionare un tipo di modifica per ogni colonna delle dimensioni a modifica lenta.  
  
 Per ulteriori informazioni su questa procedura guidata, vedere [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Colonne dimensione**  
 Consente di selezionare una colonna nell'elenco.  
  
 **Tipo di modifica**  
 Consente di selezionare un **Attributo fisso**o uno dei due tipi di attributi modificabili. Utilizzare **Attributo fisso** quando il valore di una colonna non deve cambiare. Le modifiche verranno trattate come errori in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] . Utilizzare **Attributo modificabile** per sovrascrivere i valori esistenti con i valori modificati. Utilizzare **Attributo cronologico** per salvare i valori modificati in nuovi record, contrassegnando contemporaneamente i record precedenti come obsoleti.  
  
 **Rimuovi**  
 Consente di selezionare una colonna delle dimensioni e di rimuoverla dall'elenco di colonne mappate facendo clic su **Rimuovi**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione degli output tramite Configurazione guidata dimensioni a modifica lenta](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
