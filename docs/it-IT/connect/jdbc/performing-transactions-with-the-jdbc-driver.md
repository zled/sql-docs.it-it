---
title: Esecuzione di transazioni con il Driver JDBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: afbb776f-05dc-4e79-bb25-2c340483e401
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3cecc83cced06fcc53fcddaa365e5c04fedbf469
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="performing-transactions-with-the-jdbc-driver"></a>Esecuzione di transazioni con il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  L'elaborazione delle transazioni è un requisito indispensabile di tutte le applicazioni che devono garantire la coerenza dei dati persistenti. Con il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], l'elaborazione delle transazioni può essere eseguita in modalità locale o distribuita. Le transazioni sono moduli di esecuzione atomici, consistenti, isolati e duraturi, provvisti cioè delle cosiddette proprietà ACID.  
  
 Negli argomenti di questa sezione viene descritto in che modo il driver JDBC supporta le transazioni e i livelli di isolamento, i punti di salvataggio delle transazioni e la trattenibilità dei set di risultati.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Informazioni sulle transazioni](../../connect/jdbc/understanding-transactions.md)|Fornisce una panoramica del modo in cui vengono utilizzate le transazioni con il driver JDBC.|  
|[Informazioni sulle transazioni XA](../../connect/jdbc/understanding-xa-transactions.md)|Fornisce una panoramica del modo in cui vengono utilizzate le transazioni XA con il driver JDBC.|  
|[Informazioni sui livelli di isolamento](../../connect/jdbc/understanding-isolation-levels.md)|Descrive i diversi livelli di isolamento supportati dal driver JDBC.|  
|[Uso dei punti di salvataggio](../../connect/jdbc/using-savepoints.md)|Descrive come utilizzare il driver JDBC con i punti di salvataggio delle transazioni.|  
|[Uso della trattenibilità](../../connect/jdbc/using-holdability.md)|Descrive come utilizzare il driver JDBC con la trattenibilità dei set di risultati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
