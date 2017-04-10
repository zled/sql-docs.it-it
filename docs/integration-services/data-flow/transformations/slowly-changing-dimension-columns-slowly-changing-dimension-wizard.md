---
title: "Colonne dimensioni a modifica lenta (Configurazione guidata dimensioni a modifica lenta) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.loaddimwizard.scdsupport.f1"
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Colonne dimensioni a modifica lenta (Configurazione guidata dimensioni a modifica lenta)
  Utilizzare la finestra di dialogo **Colonne dimensioni a modifica lenta** per selezionare un tipo di modifica per ogni colonna delle dimensioni a modifica lenta.  
  
 Per ulteriori informazioni su questa procedura guidata, vedere [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## Opzioni  
 **Colonne dimensione**  
 Consente di selezionare una colonna nell'elenco.  
  
 **Tipo di modifica**  
 Consente di selezionare un **Attributo fisso** o uno dei due tipi di attributi modificabili. Utilizzare **Attributo fisso** quando il valore di una colonna non deve cambiare. Le modifiche verranno trattate come errori in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] . Utilizzare **Attributo modificabile** per sovrascrivere i valori esistenti con i valori modificati. Utilizzare **Attributo cronologico** per salvare i valori modificati in nuovi record, contrassegnando contemporaneamente i record precedenti come obsoleti.  
  
 **Rimuovi**  
 Consente di selezionare una colonna delle dimensioni e di rimuoverla dall'elenco di colonne mappate facendo clic su **Rimuovi**.  
  
## Vedere anche  
 [Configurazione degli output tramite Configurazione guidata dimensioni a modifica lenta](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  