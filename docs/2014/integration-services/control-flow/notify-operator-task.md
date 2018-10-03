---
title: Attività Notifica operatori | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.notifyoperatortask.f1
helpviewer_keywords:
- Notify Operator task
- notifications [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cf995752f09f78b9727a14c19df1f57069ddb7c9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222471"
---
# <a name="notify-operator-task"></a>Notifica operatori - attività
  L'attività Notifica operatori consente di inviare messaggi di notifica agli operatori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Un operatore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent è l'alias di una persona o di un gruppo che può ricevere notifiche elettroniche. Per altre informazioni sugli operatori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vedere [Operatori](../../ssms/agent//operators.md).  
  
 Grazie all'attività Notifica operatori, con un pacchetto possono essere inviate notifiche a uno o più operatori tramite posta elettronica, cercapersone o **Net Send**. Ogni operatore può ricevere notifiche tramite metodi diversi. È ad esempio possibile usare la posta elettronica e il cercapersone per inviare notifiche a OperatorA e usare il cercapersone e **Net Send**per inviare notifiche a OperatorB. Gli operatori che ricevono notifiche dall'attività devono essere membri della raccolta **OperatorNotify** per l'attività Notifica operatori.  
  
 L'attività Notifica operatori è l'unica attività di manutenzione del database che non incapsula istruzioni Transact-SQL o comandi DBCC.  
  
## <a name="configuration-of-the-notify-operator-task"></a>Configurazione dell'attività Notifica operatori  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Questa attività è disponibile nella sezione **Attività di manutenzione** della **casella degli strumenti** di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Attività Notifica operatori &#40;Piano di manutenzione&#41;](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)  
  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostare le proprietà di un'attività o di un contenitore](../set-the-properties-of-a-task-or-container.md)  
  
  
