---
title: Classe SQLServerDataSourceObjectFactory | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 19f81b3a458ac0fa2d5e276858fcff45eeb0eb4b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverdatasourceobjectfactory-class"></a>Classe SQLServerDataSourceObjectFactory
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta una object factory per la materializzazione delle origini dati dall'interfaccia JNDI (Java Naming and Directory Interface).  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** lang  
  
 **Implementa:** javax.naming.spi. ObjectFactory  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo viene ereditato da tutte le classi dell'origine dati. Come parte del supporto per l'interfaccia Referenceable, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] espone questa classe che implementa un ObjectFactory. Server applicazioni Java chiameranno getReference in una classe di origine dati e verrà creato un oggetto di riferimento che utilizzerà il nome di classe internamente come relativa class factory.  
  
 Quando il Server applicazioni Java deve dereferenziare l'oggetto di riferimento, crea un'istanza dell'oggetto di SQLServerDataSourceObjectFactory e le chiamate di [getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md) (metodo), passando l'oggetto di riferimento, a recuperare l'istanza dell'origine dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
