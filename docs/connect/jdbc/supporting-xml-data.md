---
title: Supporto dei dati XML | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 32b7217e-1f0c-473d-9a45-176daa81584e
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 56c724017d364f3e581a6f4add22ece0091a2406
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="supporting-xml-data"></a>Supporto dei dati XML
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] fornisce un **xml** tipo di dati che consente di archiviare documenti XML e frammenti un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. Il **xml** tipo di dati è un tipo di dati incorporati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ed è simile ad altri tipi predefiniti, quali **int** e **varchar**. Come altri tipi predefiniti, è possibile utilizzare il **xml** del tipo di dati come: un tipo di variabile, un tipo di parametro, un tipo restituito dalla funzione o una colonna di tipo quando si crea una tabella o nella [!INCLUDE[tsql](../../includes/tsql_md.md)] funzioni CAST e CONVERT. Nel driver JDBC, il **xml** tipo di dati può essere eseguito come una stringa, matrice di byte, flusso, l'oggetto CLOB, BLOB oppure SQLXML. Il mapping predefinito è come stringa.  
  
 Con il driver JDBC viene fornito il supporto per l'API di JDBC 4.0, in cui viene presentata l'interfaccia SQLXML. Tale interfaccia definisce i metodi per interagire e modificare i dati XML. Il **SQLXML** è un tipo di dati JDBC 4.0 e viene eseguito il mapping di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **xml** tipo di dati. Per utilizzare il tipo di dati SQLXML nelle applicazioni, è necessario impostare il classpath in modo da includere il file sqljdbc4.jar. Se l'applicazione tenta di utilizzare il file sqljdbc3.jar durante l'accesso all'oggetto SQLXML o ai relativi metodi, verrà generata un'eccezione.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] i dati XML vengono sempre convalidati prima di essere archiviati nella colonna del database. Le applicazioni possono utilizzare **SQLXML** il tipo di dati, perché il driver JDBC per viene eseguito il mapping di **xml** automaticamente del tipo di dati. Il **SQLXML** supporto è disponibile in sqljdbc4.jar. Vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md) per l'elenco di versioni JRE supportate dal [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 Negli argomenti di questa sezione vengono descritti l'interfaccia SQLXML e come programmare con il **SQLXML** il tipo di dati utilizzando i metodi dell'API di JDBC.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Interfaccia SQLXML](../../connect/jdbc/sqlxml-interface.md)|Vengono descritti l'interfaccia SQLXML e i relativi metodi.|  
|[Programmazione con SQLXML](../../connect/jdbc/programming-with-sqlxml.md)|Viene descritto come utilizzare il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] metodi API per archiviare e recuperare i dati XML in e da un database relazionale con il **SQLXML** tipo di dati Java. Sono inoltre contenute informazioni sui tipi di oggetti SQLXML e vengono elencate importanti linee guida e limitazioni da prendere in considerazione quando si utilizzano oggetti SQLXML.|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sui tipi di dati del driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
