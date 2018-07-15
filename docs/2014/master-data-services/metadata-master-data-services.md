---
title: Metadati (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined metadata [Master Data Services], about user-defined metadata
- metadata [Master Data Services], about metadata
- metadata [Master Data Services]
- user-defined metadata [Master Data Services]
ms.assetid: ac1aabe3-d8d4-4d7a-8954-50ee3c185d81
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 19e3cde73564540b44c49536da008fa4aa54e348
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296681"
---
# <a name="metadata-master-data-services"></a>Metadati (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] i metadati definiti dall'utente sono informazioni utilizzate per descrivere gli oggetti modello. È ad esempio possibile tenere traccia dei proprietari di un particolare modello o entità oppure dei sistemi di origine tramite cui vengono forniti dati a un'entità.  
  
 Metadati definiti dall'utente sono gestiti da un modello chiamato **metadati**. Questo modello viene incluso automaticamente durante [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] è installato, ed è simile a tutti gli altri modelli MDS, ad eccezione del fatto che non è possibile creare le relative versioni.  
  
 Dopo aver popolato il modello Metadati con metadati definiti dall'utente, è possibile includerlo nelle viste sottoscrizioni, in modo che possa essere utilizzato dai sistemi di sottoscrizione.  
  
## <a name="metadata-entities"></a>Entità dei metadati  
 Nel modello Metadati sono incluse cinque entità, ognuna delle quali rappresenta un tipo di oggetto modello di dati master che supporta i metadati definiti dall'utente. Ad esempio, il **definizione metadati modello** entità contiene membri che rappresentano modelli e il **definizione metadati attributo** entità contiene membri che rappresentano tutti gli attributi in tutti i modelli.  
  
 Per definire i metadati per un oggetto modello, è necessario popolare uno di questi attributi del membro. Ad esempio, nelle **definizione metadati entità** entità, è possibile popolare l'attributo Description del membro Price con il testo: **il prezzo del prodotto quando è venduto a un cliente**.  
  
 I membri nel modello Metadati vengono aggiornati automaticamente ogni volta che gli oggetti modello che supportano i metadati definiti dall'utente vengono aggiunti o eliminati.  
  
 Non è possibile controllare la versione, aggiungere o modificare i flag di versione oppure salvare il modello Metadati come pacchetto di distribuzione. Tuttavia, sono disponibili le stesse funzionalità degli altri modelli di dati master. È ad esempio possibile implementare un set di regole business sul modello di metadati per applicare i criteri dati.  
  
## <a name="customizing-your-metadata-model"></a>Personalizzazione del modello dei metadati  
 Ciascuna entità di definizione dei metadati include gli attributi Name, Code e Description. È necessario creare attributi aggiuntivi per descrivere ulteriormente gli oggetti modello.  
  
 Può, ad esempio, essere necessario creare:  
  
-   Un attributo basato su dominio chiamato Owner da utilizzare per tenere traccia del proprietario di ciascun oggetto modello.  
  
-   Un attributo in formato libero chiamato Last Review Date da utilizzare per tenere traccia dell'ultima data in cui un oggetto è stato rivisto dal proprietario.  
  
-   Un attributo basato su dominio denominato Sources da utilizzare per tenere traccia e gestire i sistemi di origine che interagiscono con il [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] istanza.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Aggiungere metadati a un oggetto modello.|[Aggiungere metadati &#40;Master Data Services&#41;](add-metadata-master-data-services.md)
)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Esportazione di dati &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)  
  
  
