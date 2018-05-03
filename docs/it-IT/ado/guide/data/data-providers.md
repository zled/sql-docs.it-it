---
title: Provider di dati | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 877b9f25-60c4-4ab6-8052-2c28a3849e89
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c92245f0504d5531235c5e5a33f8bf5b04362b10
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-providers"></a>Provider di dati
Provider di dati rappresentano diverse origini dei dati, ad esempio database SQL, file sequenziali indicizzati, fogli di calcolo, archivi di documenti e file di posta elettronica. Provider di espongono i dati in modo uniforme utilizzando un'astrazione comune, definita set di righe.  
  
 ADO è potente e flessibile perché può connettersi a uno di diversi provider di dati diversi ed esporre il modello di programmazione stesso, indipendentemente dalle caratteristiche specifiche di qualsiasi provider specificato. Tuttavia, poiché ogni provider di dati è univoco, come l'applicazione interagisca con ADO possono variare da provider di dati.  
  
 Ad esempio, le funzionalità e caratteristiche del Provider OLE DB per SQL Server, che viene utilizzato per accedere ai database di Microsoft SQL Server, sono notevolmente diversi da quelli del Provider Microsoft OLE DB per Internet Publishing, viene utilizzato per accedere a file Archivia in un server Web.
