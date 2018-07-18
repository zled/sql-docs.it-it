---
title: Provider di dati | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 26f220f166e2269e59665a64c6e69504f298c5a9
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270700"
---
# <a name="data-providers"></a>Provider di dati
Provider di dati rappresentano diverse origini dei dati, ad esempio database SQL, file sequenziali indicizzati, fogli di calcolo, archivi di documenti e file di posta elettronica. Provider di espongono i dati in modo uniforme utilizzando un'astrazione comune, definita set di righe.  
  
 ADO è potente e flessibile perché può connettersi a uno di diversi provider di dati diversi ed esporre il modello di programmazione stesso, indipendentemente dalle caratteristiche specifiche di qualsiasi provider specificato. Tuttavia, poiché ogni provider di dati è univoco, come l'applicazione interagisca con ADO possono variare da provider di dati.  
  
 Ad esempio, le funzionalità e caratteristiche del Provider OLE DB per SQL Server, che viene utilizzato per accedere ai database di Microsoft SQL Server, sono notevolmente diversi da quelli del Provider Microsoft OLE DB per Internet Publishing, viene utilizzato per accedere a file Archivia in un server Web.
