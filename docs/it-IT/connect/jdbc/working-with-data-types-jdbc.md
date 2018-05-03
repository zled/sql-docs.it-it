---
title: Utilizzo di tipi di dati (JDBC) | Documenti Microsoft
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
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e267465de5b8fe51a1ae6aa3e3e2f371840e6d6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-data-types-jdbc"></a>Utilizzo dei tipi di dati (JDBC)
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  La funzione principale del [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] è consentire agli sviluppatori Java di accedere ai dati contenuti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. A tale scopo, il driver JDBC consente di eseguire la conversione tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati e tipi di linguaggio Java e gli oggetti.  
  
> [!NOTE]  
>  Per una descrizione dettagliata del [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e tipi di dati del driver JDBC, incluse le relative differenze e come vengono convertiti in tipi di dati del linguaggio Java, vedere [informazioni sui tipi di dati del Driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
 Per poter funzionare con i tipi di dati di SQL Server, il driver JDBC fornisce get\<tipo > e impostare\<tipo > metodi per il [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) e [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classi e fornisce get\<tipo > e aggiornare\<tipo > metodi per il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe. Il metodo da adottare dipende dal tipo di dati che si sta utilizzando e dall'eventuale utilizzo di set di risultati o query.  
  
 Negli argomenti di questa sezione viene illustrato come utilizzare i tipi di dati del driver JDBC per accedere a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dati nelle applicazioni Java.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Esempio di tipi di dati di base](../../connect/jdbc/basic-data-types-sample.md)|Viene descritto come utilizzare i metodi di richiamo del set di risultati per recuperare base [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] del tipo di dati, valori e come utilizzare i metodi di aggiornamento di set di risultati per aggiornare tali valori.|  
|[Esempio di tipo di dati SQLXML](../../connect/jdbc/sqlxml-data-type-sample.md)|Viene descritto come archiviare dati XML in un database relazionale, come recuperare i dati XML da un database e come analizzare i dati XML con il **SQLXML** tipo di dati Java.|  
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni di esempio del driver JDBC](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
