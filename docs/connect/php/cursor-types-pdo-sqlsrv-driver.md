---
title: Tipi di cursore (Driver PDO_SQLSRV) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ea6a6e-78d4-40f8-85eb-180b527f0537
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fef4910ae38fba0d101e95e9f7ad0c73d4541b72
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="cursor-types-pdosqlsrv-driver"></a>Tipi di cursore (Driver PDO_SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Il driver PDO_SQLSRV consente di creare set di risultati scorrevoli con uno dei cursori diversi.  
  
Per informazioni su come specificare un cursore utilizzando il driver PDO_SQLSRV e per esempi di codice, vedere [PDO:: Prepare](../../connect/php/pdo-prepare.md).  
  
## <a name="pdosqlsrv-and-server-side-cursors"></a>PDO_SQLSRV e i cursori sul lato Server  
Prima versione 3.0 del [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], il driver PDO_SQLSRV ha consentito di creare un set di risultati con un cursore forward-only o statico sul lato server. A partire dalla versione 3.0 del [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], keyset e cursori dinamici sono disponibili.  
  
È possibile indicare il tipo di cursore sul lato server usando PDO:: Prepare o pdostatement:: SetAttribute per selezionare un tipo di cursore:  
  
-   PDO:: ATTR_CURSOR = &GT; PDO:: CURSOR_FWDONLY  
  
-   PDO:: ATTR_CURSOR = &GT; PDO:: CURSOR_SCROLL  
  
È possibile richiedere un cursore keyset o dinamico, specificando PDO:: attr_cursor = > PDO:: cursor_scroll e quindi passare il valore appropriato per PDO:: sqlsrv_attr_cursor_scroll_type. È possibile passare a PDO:: sqlsrv_attr_cursor_scroll_type i valori possibili sono:  
  
-   PDO::SQLSRV_CURSOR_BUFFERED  
  
-   PDO::SQLSRV_CURSOR_DYNAMIC  
  
-   PDO::SQLSRV_CURSOR_KEYSET_DRIVEN  
  
-   PDO::SQLSRV_CURSOR_STATIC  
  
## <a name="pdosqlsrv-and-client-side-cursors"></a>PDO_SQLSRV e i cursori sul lato Client  
I cursori sul lato client sono stati aggiunti nella versione 3.0 del [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] che consente di memorizzare nella cache un intero set di risultati in memoria. Un vantaggio consiste nel fatto che il numero di riga è disponibile dopo l'esecuzione di una query.  
  
Cursori sul lato client devono essere utilizzati per set di risultati di piccole e medie. Set di risultati di grandi dimensioni devono utilizzare cursori sul lato server.  
  
Una query restituirà false se il buffer non è sufficientemente grande da contenere un intero set di risultati quando utilizza un cursore sul lato client. È possibile aumentare le dimensioni del buffer fino al limite di memoria PHP.  
  
È possibile configurare le dimensioni del buffer che contiene il set di risultati con l'attributo PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE [PDO:: SetAttribute](../../connect/php/pdo-setattribute.md) o [pdostatement:: SetAttribute](../../connect/php/pdostatement-setattribute.md). È inoltre possibile impostare le dimensioni massime del buffer nel file php.ini con pdo_sqlsrv.client_buffer_max_kb_size (ad esempio, pdo_sqlsrv.client_buffer_max_kb_size = 1024).  
  
Indicare che si desidera un cursore sul lato client usando PDO:: Prepare o pdostatement:: SetAttribute e selezionare il PDO:: attr_cursor = > PDO:: cursor_scroll tipo di cursore.  Specificare quindi PDO:: sqlsrv_attr_cursor_scroll_type = > PDO::SQLSRV_CURSOR_BUFFERED.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_BUFFERED));  
$stmt->execute();  
print $stmt->rowCount();  
  
echo "\n";  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
echo "\n..\n";  
  
$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );  
print "$row[Name]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );  
print "$row[1]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );  
print "$row[1]..\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );  
print_r($row);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Specifica di un tipo di cursore e selezione di righe](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)  
  
