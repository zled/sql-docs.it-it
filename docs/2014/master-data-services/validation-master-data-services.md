---
title: Convalida (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 98eb49e7-b190-4a21-8316-08c07cde14ed
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: e7a7ad1f7eada2cfa1276b76bee759fd04cfce5f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128241"
---
# <a name="validation-master-data-services"></a>Convalida (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], i dati sono convalidati per assicurare l'accuratezza. Una convalida viene eseguita automaticamente, mentre l'altra convalida è basata sulle regole business create dagli amministratori.  
  
## <a name="when-data-validation-occurs"></a>Quando viene eseguita la convalida dei dati  
 La convalida viene eseguita in momenti diversi ed è visualizzata in modo diverso nell'applicazione Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
|Tipo di convalida|Standard determinati da|Quando viene eseguita|Visualizzata nella interfaccia utente Web di Gestione dati master come|Visualizzata nel componente aggiuntivo per Excel come|I dati vengono salvati nel database MDS?|  
|---------------------|-----------------------------|--------------------|---------------------------------------------------|-------------------------------------------|------------------------------------------|  
|Convalida delle regole business|Un amministratore MDS|Automaticamente quando un utente aggiunge o modifica dati.<br /><br /> Manualmente quando un utente applica regole business.<br /><br /> Manualmente quando un amministratore nell'area funzionale **Gestione versioni** dell'applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] convalida una versione rispetto alle regole di business.|Errori di convalida|ValidationStatus|Sì|  
|Tipo di dati e convalida del contenuto|Un amministratore MDS, in caso di creazione di oggetti modello (ad esempio, la lunghezza di un attributo o il tipo di dati)|Automaticamente quando un utente aggiunge o modifica dati|Errori di input|InputStatus|no|  
|Tipo di dati e convalida del contenuto|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Oppure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Automaticamente quando un utente aggiunge o modifica dati|Errori di input|InputStatus|no|  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare regole business e pubblicarle, in modo che i dati vengano convalidati rispetto a tali regole.|[Creare e pubblicare una regola Business &#40;Master Data Services&#41;](create-and-publish-a-business-rule-master-data-services.md)|  
|Convalidare una versione di dati rispetto a regole business. Solo amministratori.|[Convalidare una versione rispetto alle regole Business &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)|  
|Convalidare un subset specifico di dati rispetto a regole business. Tutti gli utenti con l'autorizzazione per l'area funzionale **Visualizzatore** .|[Convalidare membri specifici rispetto a regole Business &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|Convalidare un subset specifico di dati rispetto a regole business. Tutti gli utenti con l'autorizzazione per l'area funzionale **Visualizzatore** e che usano [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].|[Applicare le regole di Business &#40;componente aggiuntivo MDS per Excel&#41;](microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Le regole di business &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
