---
title: La modalità di invio dei valori Java.SQL. Time al Server di configurazione | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 07eb00dd-621a-46f9-a5a5-8cab4d6058b5
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e2e91550767715616599c2720c99b864363a185
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32831966"
---
# <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Configurazione della modalità di invio dei valori java.sql.Time al server
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Se si utilizza un oggetto java.SQL. Time o il tipo JDBC java.sql.Types.TIME per impostare un parametro, è possibile configurare come il valore Java.SQL. Time viene inviato al server. come un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **ora** tipo o come un **datetime** tipo.  
  
 Questo scenario si applica quando si utilizza uno dei seguenti metodi:  
  
-   [SQLServerCallableStatement.registerOutParameter (int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int.md)  
  
-   [SQLServerCallableStatement.registerOutParameter (int, int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int-int.md)  
  
-   [SQLServerCallableStatement.setTime](../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setTime](../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)  
  
-   [SQLServerCallableStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)  
  
 È possibile configurare come il valore Java.SQL. Time viene inviato tramite il **sendTimeAsDatetime** proprietà di connessione. Per ulteriori informazioni, vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).  
  
 A livello di codice è possibile modificare il valore di **sendTimeAsDatetime** proprietà di connessione con [Setsendtimeasdatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] anteriore [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] non supportano il **ora** come valori di tipo di dati, pertanto le applicazioni utilizzano Java.SQL. Time in genere archiviano Java.SQL **datetime** o **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati.  
  
 Se si desidera utilizzare il **datetime** e **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati quando si lavora con i valori Java.SQL. Time, è necessario impostare il **sendTimeAsDatetime** proprietà di connessione su **true**. Se si desidera utilizzare il **ora** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] del tipo di dati quando utilizza valori Java.SQL. Time, è necessario impostare il **sendTimeAsDatetime** proprietà di connessione su **false**.  
  
 Tenere presente che quando inviano valori Java.SQL. Time in un parametro il cui tipo di dati può archiviare anche la data, tali date predefinite sono diverse a seconda se il valore Java.SQL. Time viene inviato come un **datetime** (1/1/1970) o **ora** valore (1/1/1900). Per ulteriori informazioni sulle conversioni dei dati quando si inviano dati a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere [utilizzando dati di data e ora](http://go.microsoft.com/fwlink/?LinkID=145211).  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Driver JDBC 3.0 **sendTimeAsDatetime** è true per impostazione predefinita. In una versione futura, il **sendTimeAsDatetime** proprietà di connessione può essere impostata su false per impostazione predefinita.  
  
 Per assicurarsi che l'applicazione continui a funzionare come previsto, indipendentemente dal valore predefinito del **sendTimeAsDatetime** proprietà di connessione, è possibile:  
  
-   Utilizzare Java.SQL. quando si lavora con la **ora** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati.  
  
-   Utilizzare Java.SQL. timestamp quando si lavora con la **datetime**, **smalldatetime**, e **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati.  
  
Si noti che sendTimeAsDatetime deve essere false per le colonne crittografate come colonne crittografate non supportano la conversione da ora in datetime. A partire da Microsoft JDBC Driver 6.0 per SQL Server, la classe SQLServerConnection dispone di due metodi seguenti per il valore della proprietà sendTimeAsDatetime set/get.

```
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sui tipi di dati del driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
