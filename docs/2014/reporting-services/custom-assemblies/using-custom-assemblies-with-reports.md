---
title: Uso di assembly personalizzati con i report | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d0ab2fc2b4411fa97f99b2888142ad7783d9b514
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219441"
---
# <a name="using-custom-assemblies-with-reports"></a>Utilizzo di assembly personalizzati con i report
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è possibile scrivere codice personalizzato per i valori, gli stili e la formattazione degli elementi dei report. È ad esempio possibile utilizzare il codice personalizzato per formattare le valute in base alle impostazioni locali, per contrassegnare determinati valori con una formattazione speciale o per applicare altre regole di business in uso nella società. Un metodo per includere questo codice nei report consiste nel creare un assembly di codice personalizzato usando [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], a cui sia possibile fare riferimento dai file di definizione del report. Il server chiama le funzioni degli assembly personalizzati durante l'esecuzione di un report. Gli assembly personalizzati possono essere utilizzati per recuperare funzioni specifiche che si intende utilizzare nei report.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Riferimento agli assembly in un file RDL](referencing-assemblies-in-an-rdl-file.md)  
 Viene descritto come fare riferimento agli assembly personalizzati in un file RDL (Report Definition Language).  
  
 [Distribuzione di un assembly personalizzato](deploying-a-custom-assembly.md)  
 Viene descritto come distribuire un assembly personalizzato in Progettazione report e nel server di report.  
  
 [Uso di assembly personalizzati con nome sicuro](using-strong-named-custom-assemblies.md)  
 Viene descritto come utilizzare gli assembly personalizzati con nomi sicuri.  
  
 [Asserzione di autorizzazioni negli assembly personalizzati](asserting-permissions-in-custom-assemblies.md)  
 Viene descritto come distribuire assembly personalizzati con autorizzazioni limitate e specifiche e come effettuare l'asserzione di tali autorizzazioni nel codice.  
  
 [Accesso agli assembly personalizzati tramite espressioni](accessing-custom-assemblies-through-expressions.md)  
 Viene descritto come chiamare metodi di assembly personalizzati come espressioni di report nelle definizioni del report.  
  
 [Inizializzazione di oggetti assembly personalizzati](initializing-custom-assembly-objects.md)  
 Viene descritto come inizializzare i valori per gli oggetti degli assembly personalizzati chiamati da un report.  
  
 [Procedura: Debug di assembly personalizzati](how-to-debug-custom-assemblies.md)  
 Viene descritto come eseguire il debug del codice dell'assembly personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Report Definition Language &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md)  
  
  
