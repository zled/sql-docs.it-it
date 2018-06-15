---
title: Pool di connessioni (driver Microsoft per PHP per SQL Server) | Documenti Microsoft
ms.custom: ''
ms.date: 07/10/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb23d95aeebfbc44db876d64a96add890d17e806
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307180"
---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>Pool di connessioni (Driver Microsoft per PHP per SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Di seguito vengono segnalati aspetti importanti da tenere presenti circa il pool di connessioni nei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]:  
  
-   I [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] usano i pool di connessioni ODBC.  
  
-   Per impostazione predefinita, il pool di connessioni è abilitato in Windows. In Linux e Mac OS X, le connessioni sono in pool solo se il pool di connessioni è abilitato per ODBC. Quando il pool di connessioni è abilitato e si connette a un server, il driver tenta di usare una connessione in pool prima di crearne uno nuovo. Se nel pool non viene trovata una connessione equivalente, una nuova connessione viene creata e aggiunta al pool. Il driver determina se le connessioni sono equivalenti confrontando le stringhe di connessione.  
  
-   Quando si usa una connessione del pool, lo stato della connessione viene ripristinato.  
  
-   Quando si chiude la connessione, questa viene riportata al pool.  
  
Per ulteriori informazioni sui pool di connessioni, vedere [pool di connessioni di gestione Driver](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="enablingdisabling-connection-pooling"></a>Il pool di connessioni di abilitazione/disabilitazione
### <a name="windows"></a>Windows
È possibile forzare il driver a creare una nuova connessione (anziché cercarne una connessione equivalente nel pool di connessioni) impostando il valore di *ConnectionPooling* attributo nella stringa di connessione per **false**  (o 0).  
  
Se il *ConnectionPooling* attributo viene omesso dalla stringa di connessione o se è impostato su **true** (o 1), il driver crea una nuova connessione solo se non esiste una connessione equivalente nel pool di connessioni.  
  
Per informazioni sugli altri attributi di connessione, vedere [Connection Options](../../connect/php/connection-options.md).  
### <a name="linux-and-mac-os-x"></a>Linux e Mac OS X
*ConnectionPooling* attributo non può essere utilizzato per attivare/disattivare il pool di connessioni. 

Il pool di connessioni può essere abilitato o disabilitato, modificando il file di configurazione odbcinst.ini. Il driver deve essere ricaricato rendere effettive le modifiche.

Impostazione `Pooling` a `Yes` e positivo `CPTimeout`valore odbcinst.ini consente il pool di connessioni. 
```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
CPTimeout=<int value>
```
Impostazione `Pooling` a `No` in odbcinst.ini forza il driver a creare una nuova connessione.
```
[ODBC]
Pooling=No
```
  
## <a name="see-also"></a>Vedere anche  
[Procedura: Connessione con l'autenticazione di Windows](../../connect/php/how-to-connect-using-windows-authentication.md)

[Procedura: Connessione con l'autenticazione di SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
  
