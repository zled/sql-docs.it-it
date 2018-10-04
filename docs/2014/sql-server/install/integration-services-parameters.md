---
title: Parametri di Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b2b9fc62d26edbac0244bed07d20931fbb508f8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210381"
---
# <a name="integration-services-parameters"></a>Parametri di Integration Services
  Per la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], è possibile decidere di analizzare [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pacchetti nel computer, o [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] file del pacchetto nel file system. Se si sceglie di analizzare i file nel file system, specificare il percorso della cartella che contiene i pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Opzioni  
 **Analizza pacchetti SSIS nel Computer**  
 Selezionare questa opzione per analizzare i pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nel computer. Per impostazione predefinita, questa opzione è selezionata.  
  
 **Analizza file pacchetti SSIS**  
 Selezionare questa opzione per analizzare i pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nel file system.  
  
 **Percorso pacchetti SSIS**  
 Individuare il percorso UNC o locale in cui sono memorizzati i pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Non è necessario includere i nomi di file. Se il percorso immesso non è accessibile, è possibile fare clic su **successivo**. Per impostazione predefinita, il percorso è vuoto. Questo campo è abilitato solo quando si seleziona **Analizza file pacchetti SSIS**.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di preparazione aggiornamento](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Riferimento all'interfaccia utente di preparazione aggiornamento](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
