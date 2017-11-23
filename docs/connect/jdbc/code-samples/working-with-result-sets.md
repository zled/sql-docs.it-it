---
title: Utilizzo di set di risultati | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.openlocfilehash: 840bf63c87a6f6b91e1be3afb690ca62906dc703
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="working-with-result-sets"></a>Utilizzo dei set di risultati
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Quando si utilizzano i dati contenuti in un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database, un metodo di manipolazione dei dati consiste nell'utilizzare un set di risultati. Il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] supporta l'utilizzo del risultato set tramite la [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto. Tramite l'oggetto SQLServerResultSet, può recuperare i dati restituiti da un'istruzione SQL o stored procedure, aggiornare i dati in base alle esigenze e quindi inviare nuovamente i dati al database.  
  
 Inoltre, l'oggetto SQLServerResultSet fornisce metodi per la navigazione nelle righe di dati, recupero o impostazione dei dati in esso contenuti e per la creazione di vari livelli di sensibilità alle modifiche nel database sottostante.  
  
> [!NOTE]  
>  Per ulteriori informazioni sulla gestione di set di risultati, inclusa la sensibilità alle modifiche, vedere [gestione dei set di risultati con il Driver JDBC](../../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
 Negli argomenti di questa sezione vengono descritti diversi modi, che è possibile utilizzare un set di risultati per manipolare i dati contenuti un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Esempio di recupero dei dati del set di risultati](../../../connect/jdbc/retrieving-result-set-data-sample.md)|Viene descritto come utilizzare un set di risultati per recuperare dati da un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database e la Visualizza.|  
|[Esempio di modifica dei dati dei set di risultati](../../../connect/jdbc/modifying-result-set-data-sample.md)|Viene descritto come utilizzare un set di risultati per inserire, recuperare e modificare i dati in un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database.|  
|[Esempio di memorizzazione nella cache dei dati dei set di risultati](../../../connect/jdbc/caching-result-set-data-sample.md)|Viene descritto come utilizzare un set di risultati per recuperare grandi quantità di dati da un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database e per controllare come vengono memorizzati i dati nel client.|  
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni di esempio del driver JDBC](../../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
