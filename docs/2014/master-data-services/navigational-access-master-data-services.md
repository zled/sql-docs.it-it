---
title: Accesso per la navigazione (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 20f3e8f8d51231f823fe43a8aeff4e606a10ffa2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087201"
---
# <a name="navigational-access-master-data-services"></a>Accesso per la navigazione (Master Data Services)
  L'accesso per la navigazione si applica alla sicurezza dell'oggetto modello, assegnata nella scheda **Modelli**.  
  
 L'accesso per la navigazione è l'accesso che si ottiene ai livelli superiori a quello per cui è stata assegnata la sicurezza.  
  
 In questo esempio le autorizzazioni vengono assegnate a un'entità, pertanto l'accesso per la navigazione viene concesso a livello di modello.  
  
 ![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **Entità**  
  
 Quando si assegna un'autorizzazione a un'entità, ai relativi membri foglia o membri consolidati, l'accesso per la navigazione consente di leggere o aggiornare il nome e il codice di tutti i membri. È inoltre possibile leggere il nome del modello.  
  
 **Attributi**  
  
 Quando si assegna un'autorizzazione a un attributo, l'accesso per la navigazione consente di leggere o aggiornare il nome e il codice di tutti i membri nell'entità. È inoltre possibile leggere il nome del modello.  
  
 **Raccolte**  
  
 Quando si assegnano autorizzazioni alle raccolte, è possibile leggere o aggiornare nome, codice, descrizione e ID proprietario. È inoltre possibile leggere il nome del modello.  
  
## <a name="see-also"></a>Vedere anche  
 [Come vengono determinate le autorizzazioni &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)  
  
  
