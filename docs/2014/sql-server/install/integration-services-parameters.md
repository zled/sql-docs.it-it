---
title: Parametri di Integration Services | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f178c02cc93d23a14e0fb658398e5f0ba4cf6dc0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065974"
---
# <a name="integration-services-parameters"></a>Parametri di Integration Services
  Per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], è possibile decidere di analizzare [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pacchetti nel computer, o [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] i file del pacchetto nel file system. Se si sceglie di analizzare i file nel file system, specificare il percorso della cartella che contiene i pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Opzioni  
 **Analizza pacchetti SSIS nel Computer**  
 Selezionare questa opzione per analizzare i pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nel computer. Per impostazione predefinita, questa opzione è selezionata.  
  
 **Analizza file pacchetti SSIS**  
 Selezionare questa opzione per analizzare i pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nel file system.  
  
 **Percorso pacchetti SSIS**  
 Individuare il percorso UNC o locale in cui sono memorizzati i pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Non è necessario includere i nomi di file. Se il percorso immesso non è accessibile, è possibile fare clic su **successivo**. Per impostazione predefinita, il percorso è vuoto. Questo campo è attivato solo quando si seleziona **Analizza file pacchetti SSIS**.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di preparazione aggiornamento](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Riferimento all'interfaccia utente di preparazione aggiornamento](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  