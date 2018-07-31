---
title: Classe SQLServerDataSourceObjectFactory | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ecec8f58587d6a57468f8078e1f680675bede77
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38046849"
---
# <a name="sqlserverdatasourceobjectfactory-class"></a>Classe SQLServerDataSourceObjectFactory
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta una object factory per la materializzazione delle origini dati dall'interfaccia JNDI (Java Naming and Directory Interface).  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** java.lang.Object  
  
 **Implementa:** javax.naming.spi.ObjectFactory  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>Remarks  
 Questo metodo viene ereditato da tutte le classi dell'origine dati. Come parte del supporto per l'interfaccia Referenceable, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] espone questa classe che implementa un elemento ObjectFactory. I server applicazioni Java chiameranno getReference in una classe dell'origine dati creando in questo modo un oggetto Reference che userà il nome della classe internamente come relativa class factory.  
  
 Quando il Server applicazioni Java deve dereferenziare l'oggetto di riferimento, crea un'istanza dell'oggetto di SQLServerDataSourceObjectFactory e chiama il [getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md) metodo, passando l'oggetto di riferimento, a recuperare l'istanza dell'origine dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Informazioni di riferimento sull'API del driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
