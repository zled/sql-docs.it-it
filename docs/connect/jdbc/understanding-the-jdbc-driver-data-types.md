---
title: Informazioni sui tipi di dati del Driver JDBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7802328d-4d23-4775-9573-4169b127d258
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1cd9f516a8d72aabf8b10d25b9553cf35a3be3bd
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-the-jdbc-driver-data-types"></a>Informazioni sui tipi di dati del driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]supporta l'utilizzo dei tipi di dati di base e avanzati di JDBC all'interno di un'applicazione Java che utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] come database.  
  
 Il tipo di sistema JDBC consente di eseguire la conversione tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati e tipi di linguaggio Java e gli oggetti. I tipi JDBC sono basati sui tipi SQL-92 e SQL-99. Il driver JDBC è conforme alla specifica JDBC ed è progettato per fornire il giusto equilibrio tra prevedibilità e flessibilità.  
  
 Negli argomenti di questa sezione viene descritto come utilizzare i tipi di dati di base e avanzati e viene illustrato in che modo i tipi di dati possono essere convertiti in altri tipi di dati.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Utilizzo di tipi di dati di base](../../connect/jdbc/using-basic-data-types.md)|Vengono descritti i tipi di dati JDBC di base. Sono inclusi esempi su come gestire i tipi di dati utilizzando set di risultati, query con parametri e stored procedure.|  
|[Configurare la modalità di invio dei valori Java.SQL. Time al Server](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)|Viene descritto come il driver JDBC genera le date.|  
|[Utilizzo di tipi di dati avanzati](../../connect/jdbc/using-advanced-data-types.md)|Vengono descritti i tipi di dati JDBC avanzati.|  
|[Informazioni sulle differenze tra tipi di dati](../../connect/jdbc/understanding-data-type-differences.md)|Vengono descritte le differenze tra i vari tipi di dati del driver JDBC.|  
|[Informazioni sulle conversioni di tipi di dati](../../connect/jdbc/understanding-data-type-conversions.md)|Viene descritto in che modo viene gestita la conversione dei tipi di dati quando si utilizzano i metodi di richiamo e impostazione.|  
|[Supporto del Set di caratteri nazionali](../../connect/jdbc/national-character-set-support.md)|Viene descritto il supporto per i tipi di set di caratteri nazionali.|  
|[Supporto dei dati XML](../../connect/jdbc/supporting-xml-data.md)|Viene descritta l'interfaccia SQLXML. Viene inoltre descritto come leggere e scrivere dati XML da e in un database relazionale con il **SQLXML** tipo di dati Java.|  
|[Wrapper e interfacce](../../connect/jdbc/wrappers-and-interfaces.md)|Vengono descritte le interfacce che hanno il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] specifici metodi e le costanti che consentono a un server di applicazione creare un proxy della classe, viene inoltre supporto per l'interfaccia Java.SQL.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del Driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

