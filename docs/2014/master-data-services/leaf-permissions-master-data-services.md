---
title: Autorizzazioni per elementi foglia (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e6487c15c05fa157afdb8e644ead2f692e35f6ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166643"
---
# <a name="leaf-permissions-master-data-services"></a>Autorizzazioni per elementi foglia (Master Data Services)
  Le autorizzazioni foglia si applicano ai valori di attributo per tutti i membri foglia di un'entità.  
  
 Per le entità senza gerarchie esplicite abilitate, l'assegnazione delle autorizzazioni all'elemento **Foglia** equivale all'assegnazione delle autorizzazioni all'entità.  
  
 **Note:**  
  
-   Le autorizzazioni foglia si applicano solo all'area funzionale **Visualizzatore** dell'interfaccia utente.  
  
-   Le autorizzazioni assegnate agli attributi **Name** e **Code** non sono applicate.  
  
|Autorizzazione|Description|  
|----------------|-----------------|  
|**Sola lettura**|I membri foglia vengono visualizzati, ma l'utente non può aggiungerli, rimuoverli o modificarli.<br /><br /> Se esistono membri consolidati, i nomi e i codici vengono visualizzati, ma l'utente non può aggiungerli, rimuoverli o modificarli.|  
|**Update**|I membri foglia vengono visualizzati e l'utente può aggiungerli, rimuoverli e modificarli.<br /><br /> Se esistono membri consolidati, i nomi e i codici vengono visualizzati, ma l'utente non può aggiungerli, rimuoverli o modificarli.|  
|**Nega**|I membri foglia per l'entità non vengono visualizzati.|  
  
## <a name="attribute-permissions"></a>Autorizzazioni per attributi  
 Le autorizzazioni per gli attributi si applicano ai valori degli attributi per l'entità specifica. Gli utenti che dispongono solo delle autorizzazioni per gli attributi non possono aggiungere o rimuovere membri.  
  
|Autorizzazione|Description|  
|----------------|-----------------|  
|**Sola lettura**|L'attributo viene visualizzato, ma l'utente non può modificare i valori di attributo.|  
|**Update**|L'attributo viene visualizzato e l'utente può modificare i valori di attributo.|  
|**Nega**|L'attributo non viene visualizzato.<br /><br /> Nota: non è possibile negare in modo esplicito l'accesso agli attributi Name e Code.|  
  
### <a name="example"></a>Esempio  
 Per l'entità Product, assegnare l'autorizzazione **Update** all'attributo Subcategory. Negare l'autorizzazione per tutti gli altri attributi.  
  
|nome|codice|Subcategory (Aggiornamento)|  
|----------|----------|----------------------------|  
|Mountain-100|BK-M101|{5} Mountain Bikes|  
|Mountain-100|BK-M201|{5} Mountain Bikes|  
  
 Nel **Visualizzatore**è possibile aggiornare qualsiasi valore di attributo nella colonna Subcategory. Se non si dispone delle autorizzazioni per un attributo, l'attributo non viene visualizzato.  
  
> [!NOTE]  
>  In questo esempio, Subcategory è un attributo basato su dominio, basato sull'entità SubcategoryList. È possibile selezionare una sottocategoria diversa per Mountain-100, ma non è possibile aggiungere o eliminare membri dall'entità SubcategoryList.  
  
## <a name="see-also"></a>Vedere anche  
 [Assegnare autorizzazioni per oggetti modello &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Consolidare le autorizzazioni &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)   
 [Autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Membri &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Gli attributi &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  