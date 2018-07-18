---
title: Ottenere informazioni da IHV - Analitica Platform System | Documenti Microsoft
description: Informazioni di ottenere il IHV sull'accessorio Analitica Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 57b61ed7741bc6d36b7531a62416893e7cc10fb7
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="information-to-obtain-from-your-ihv"></a>Informazioni di ottenere il IHV
Quando il fornitore di hardware indipendenti (IHV) recapita i nuovi accessori di SQL Server PDW all'utente, fornirà anche informazioni sull'hardware del dispositivo e la configurazione eseguono del dispositivo. È necessario che queste informazioni per l'amministrazione del dispositivo.  
  
Nell'elenco seguente mostra le informazioni necessarie in genere dal fornitore. In alcuni casi, sono necessario aggiuntive o altre informazioni. Verificare con il fornitore per verificare che tutte le informazioni pertinenti sono state trasferite all'utente con la distribuzione del dispositivo.  
  
|||  
|-|-|  
|**Le informazioni o del documento**|**Description**|  
|Distinta base (BOM)|La distinta base sono elencati i componenti presenti nel dispositivo. Queste informazioni sono necessarie per confermare che tutti i componenti sono stati recapitati.<br /><br />**Importante:** distinta di base deve includere i pesi per ognuno dei nodi del dispositivo e per ogni rack completo. Queste informazioni sono importanti quando si pianifica di gestire e spostare i componenti di dispositivo e di garantire che il data center in grado di gestire il dispositivo. Se il BOM non include i pesi dei nodi, assicurarsi di ottenere queste informazioni con il fornitore per tutti i nodi.|  
|Diagrammi di cablaggi|Cablaggi diagrammi mostrano come collegare la rete, power, altri cavi e per ogni dispositivo rack. Questi diagrammi sono necessari quando si installa il dispositivo nel data center e ogni volta che è necessario rimuovere o sostituire un componente.|  
|Requisiti scaffali Appliance|Prima di poter installare il dispositivo nel data center, è necessario sapere se il data center soddisfa il flusso d'aria e requisiti di lunghezza dei cavi per il dispositivo, nonché le dimensioni e power per i componenti. Vedere anche della distinta base (BOM) sopra per informazioni sui pesi componente accessorio, che è anche necessario.|  
  
