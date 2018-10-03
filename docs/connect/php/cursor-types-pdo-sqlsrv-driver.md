---
title: Tipi di cursore (Driver PDO_SQLSRV) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 49ea6a6e-78d4-40f8-85eb-180b527f0537
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 621bfe1f20b9ca656bf442377b1f453503b86a8f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833469"
---
# <a name="cursor-types-pdosqlsrv-driver"></a>Tipi di cursore (driver PDO_SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Il driver PDO_SQLSRV consente di creare set di risultati scorrevoli con uno dei cursori diversi.  
  
Per informazioni su come specificare un cursore utilizzando il driver PDO_SQLSRV e per esempi di codice, vedere [PDO:: Prepare](../../connect/php/pdo-prepare.md).  
  
## <a name="pdosqlsrv-and-server-side-cursors"></a>PDO_SQLSRV e cursori sul lato Server  
Prima della versione 3.0 del [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], il driver PDO_SQLSRV consentiva di creare un set di risultati con un cursore forward-only o statico sul lato server. Partire dalla versione 3.0 del [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], keyset e cursori dinamici sono anche disponibili.  
  
È possibile indicare il tipo di cursore lato server con pdostatement:: SetAttribute o PDO:: Prepare per selezionare uno dei due tipi di cursore:  
  
-   PDO:: ATTR_CURSOR = &GT; PDO:: CURSOR_FWDONLY  
  
-   PDO:: ATTR_CURSOR = &GT; PDO:: CURSOR_SCROLL  
  
È possibile richiedere un cursore keyset o dynamic specificando PDO:: attr_cursor = > PDO:: cursor_scroll e quindi passare il valore appropriato per PDO:: sqlsrv_attr_cursor_scroll_type. I valori possibili che è possibile passare a PDO:: sqlsrv_attr_cursor_scroll_type sono:  
  
-   PDO::SQLSRV_CURSOR_BUFFERED  
  
-   PDO::SQLSRV_CURSOR_DYNAMIC  
  
-   PDO::SQLSRV_CURSOR_KEYSET_DRIVEN  
  
-   PDO::SQLSRV_CURSOR_STATIC  
  
## <a name="pdosqlsrv-and-client-side-cursors"></a>PDO_SQLSRV e cursori sul lato Client  
I cursori sul lato client sono stati aggiunti nella versione 3.0 del [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] che consente di memorizzare nella cache un intero set di risultati in memoria. Un vantaggio è che il numero di riga è disponibile dopo che viene eseguita una query.  
  
Usare cursori sul lato client per i set di risultati di piccole e medie. Set di risultati di grandi dimensioni devono usare cursori sul lato server.  
  
Una query restituirà false se il buffer non è sufficientemente grande da contenere un intero set di risultati quando utilizza un cursore lato client. È possibile aumentare le dimensioni del buffer fino al limite di memoria PHP.  
  
È possibile configurare le dimensioni del buffer che contiene il set di risultati con l'attributo PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE del [PDO:: SetAttribute](../../connect/php/pdo-setattribute.md) oppure [pdostatement:: SetAttribute](../../connect/php/pdostatement-setattribute.md). È anche possibile impostare la dimensione massima del buffer nel file PHP. ini con pdo_sqlsrv.client_buffer_max_kb_size (ad esempio, pdo_sqlsrv.client_buffer_max_kb_size = 1024).  
  
Indicare che si vuole un cursore lato client usando PDO:: Prepare o pdostatement:: SetAttribute e si seleziona il PDO:: attr_cursor = > PDO:: cursor_scroll il tipo di cursore.  È quindi possibile specificare PDO:: sqlsrv_attr_cursor_scroll_type = > PDO::SQLSRV_CURSOR_BUFFERED.  
  
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
  
