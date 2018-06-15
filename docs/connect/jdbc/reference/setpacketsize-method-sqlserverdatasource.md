---
title: Metodo setPacketSize (SQLServerDataSource) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08f4f72aae10fc154b7362a83e870d85b9fb42e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32844606"
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>Metodo setPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta le dimensioni di pacchetto di rete corrente utilizzata per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], specificato in byte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Dimensioni del pacchetto*  
  
 Un **int** valore contenente la dimensione del pacchetto di rete.  
  
## <a name="remarks"></a>Osservazioni  
 L'intervallo di valori accettabili di questa proprietà è [-1 | 0 | 512..32767]. Se questa proprietà è impostata su un valore che non rientra nell'intervallo valido, viene generata un'eccezione.  
  
 È possibile impostare la proprietà packetSize durante la connessione alla crittografia SSL (Secure Sockets Layer). Il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] negozia la dimensione del pacchetto con il server. Se la proprietà encrypt è impostata su "**true**" e le dimensioni del pacchetto negoziato sono maggiore di dimensioni dei record di Java Virtual Machine (JVM) del provider di sicurezza predefinito SSL, il driver genererà un errore e termina la connessione.  
  
 È inoltre possibile impostare la proprietà packetSize senza richiedere la crittografia SSL. In questo caso, se il server richiede il supporto della crittografia SSL da parte del client, il driver verificherà le dimensioni dei record SSL del provider di sicurezza predefinito di JVM. Se le dimensioni della proprietà packetSize sono superiori rispetto alle dimensioni dei record SSL del provider di sicurezza predefinito di JVM, il driver genererà un errore e terminerà la connessione.  
  
 Per ulteriori informazioni sull'utilizzo di SSL, vedere [utilizzando la crittografia SSL](../../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
