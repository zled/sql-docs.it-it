---
title: Più vincoli di precedenza | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d4a9dc0f4b40320533828e2b1ef9f5f4cdfab9c5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068967"
---
# <a name="multiple-precedence-constraints"></a>Più vincoli di precedenza
  Un vincolo di precedenza consente di connettere due eseguibili, ad esempio due attività, due contenitori o un'attività e un contenitore. Gli elementi connessi sono noti come eseguibile con precedenza ed eseguibile soggetto al vincolo. A un eseguibile soggetto a vincolo possono essere applicati più vincoli di precedenza. Per altre informazioni, vedere [Vincoli di precedenza](control-flow/precedence-constraints.md).  
  
 Raggruppando più vincoli è possibile definire scenari complessi, che consentono di implementare flussi di controllo complessi nei pacchetti. Ad esempio, nella figura seguente, attività D è collegata all'attività A da un `Success` vincolo, l'attività D è collegata all'attività B da un `Failure` vincolo e l'attività D è collegata all'attività C da un `Success` vincolo. I vincoli di precedenza tra le attività D e A, tra le attività D e B e tra le attività D e C sono legati da una relazione logica *e* . L'attività D viene quindi eseguita solo se l'attività A viene completata, l'attività B non viene eseguita e l'attività C deve essere eseguita correttamente.  
  
 ![Attività collegate in base ai vincoli di precedenza](media/precedenceconstraints.gif "Attività collegate in base ai vincoli di precedenza")  
  
## <a name="logicaland-property"></a>Proprietà LogicalAnd  
 Se a un'attività o contenitore sono applicati più vincoli, la proprietà `LogicalAnd` specificherà se il corrispondente vincolo di precedenza viene valutato singolarmente o insieme ad altri vincoli.  
  
 È possibile impostare il `LogicalAnd` proprietà utilizzando il **Editor vincoli di precedenza** in [!INCLUDE[ssIS](../includes/ssis-md.md)] finestra di progettazione o nella finestra proprietà che [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] fornisce.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Impostare le proprietà di un vincolo di precedenza](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  