---
title: Programmazione dell'agente di raccolta dati | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data collector [SQL Server], programming
ms.assetid: 53b4752b-055d-4716-b2bc-75b4cce84101
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a9a3e4428eee6057ac3e38e553eec43616504a06
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169265"
---
# <a name="data-collector-programming"></a>Programmazione dell'agente di raccolta dati
  L'API dell'agente di raccolta dati, nello spazio dei nomi <xref:Microsoft.SqlServer.Management.Collector>, consente il controllo a livello di codice di tutte le operazioni di configurazione tramite il modello a oggetti. Molte delle operazioni di raccolta dati in cui viene utilizzata l'API vengono inoltre implementate come stored procedure installate nel server.  
  
 Nell'illustrazione seguente sono riportati gli elementi principali del modello a oggetti dell'agente di raccolta dati.  
  
 ![Il modello a oggetti dell'agente di raccolta dati](../../../2014/database-engine/dev-guide/media/dc-objectmodel.gif "il modello a oggetti dell'agente di raccolta dati")  
  
  