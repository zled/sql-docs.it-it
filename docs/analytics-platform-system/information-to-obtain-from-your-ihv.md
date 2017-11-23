---
title: Informazioni di ottenere il fornitore (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bce301a-704c-4236-a0a1-851bd17e2b6c
caps.latest.revision: "11"
ms.openlocfilehash: ba945781bbcf293605aa820f7e31c1b32f6409f5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="information-to-obtain-from-your-ihv"></a>Informazioni di ottenere il IHV
Quando il fornitore di hardware indipendenti (IHV) recapita i nuovi accessori di SQL Server PDW all'utente, fornirà anche informazioni sull'hardware del dispositivo e la configurazione eseguono del dispositivo. È necessario che queste informazioni per l'amministrazione del dispositivo.  
  
Nell'elenco seguente mostra le informazioni necessarie in genere dal fornitore. In alcuni casi, sono necessario aggiuntive o altre informazioni. Verificare con il fornitore per verificare che tutte le informazioni pertinenti sono state trasferite all'utente con la distribuzione del dispositivo.  
  
|||  
|-|-|  
|**Informazioni o del documento**|**Description**|  
|Distinta base (BOM)|La distinta base sono elencati i componenti presenti nel dispositivo. Queste informazioni sono necessarie per confermare che tutti i componenti sono stati recapitati.<br /><br />**Importante:** distinta di base deve includere i pesi per tutti i nodi dello strumento e per ogni rack completo. Queste informazioni sono importanti quando si pianifica di gestire e spostare i componenti di dispositivo e di garantire che il data center in grado di gestire il dispositivo. Se il BOM non include i pesi dei nodi, assicurarsi di ottenere queste informazioni con il fornitore per tutti i nodi.|  
|Diagrammi di cablaggi|Cablaggi diagrammi mostrano come collegare la rete, power, altri cavi e per ogni dispositivo rack. Questi diagrammi sono necessari quando si installa il dispositivo nel data center e ogni volta che è necessario rimuovere o sostituire un componente.|  
|Requisiti scaffali Appliance|Prima di poter installare il dispositivo nel data center, è necessario sapere se il data center soddisfa il flusso d'aria e requisiti di lunghezza dei cavi per il dispositivo, nonché le dimensioni e power per i componenti. Vedere anche della distinta base (BOM) sopra per informazioni sui pesi componente accessorio, che è anche necessario.|  
  
