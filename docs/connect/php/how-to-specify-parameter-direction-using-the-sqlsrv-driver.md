---
title: 'Procedura: specificare la direzione del parametro usando il Driver SQLSRV | Documenti Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- stored procedure support
ms.assetid: 1209eeca-df75-4283-96dc-714f39956b95
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b4004fa498c01e73c99204bb0d36ac4bded66a9b
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-specify-parameter-direction-using-the-sqlsrv-driver"></a>Procedura: Specificare la direzione del parametro usando il driver SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento viene illustrato come usare il driver SQLSRV per specificare la direzione del parametro nella chiamata di una stored procedure. La direzione del parametro viene specificato quando si costruisce una matrice di parametri (passaggio 3) che viene passata a [sqlsrv_query](../../connect/php/sqlsrv-query.md) oppure [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md).  
  
### <a name="to-specify-parameter-direction"></a>Per specificare la direzione di un parametro  
  
1.  Definire una query Transact-SQL che chiama una stored procedure. Usare il punto interrogativo (?) anziché i parametri da passare alla stored procedure. Questa stringa, ad esempio, chiama una stored procedure, UpdateVacationHours, che accetta due parametri:  
  
    ```  
    $tsql = "{call UpdateVacationHours(?, ?)}";  
    ```  
  
    > [!NOTE]  
    > È consigliabile pertanto chiamare le stored procedure usando la sintassi canonica. Per ulteriori informazioni sulla sintassi canonica, vedere [chiamare una Stored Procedure](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md).  
  
2.  Inizializzare o aggiornare le variabili PHP che corrispondono ai segnaposto della query Transact-SQL. Ad esempio, il codice seguente consente di inizializzare i due parametri della stored procedure UpdateVacationHours:  
  
    ```  
    $employeeId = 101;  
    $usedVacationHours = 8;  
    ```  
  
    > [!NOTE]  
    > Le variabili inizializzate o aggiornate su **null**, **DateTime**o tipi di flusso non possono essere usate come parametri di output.  
  
3.  Usare le variabili PHP del passaggio 2 per creare o aggiornare una matrice di valori di parametri che corrispondono nell'ordine ai segnaposto della stringa di Transact-SQL. Specificare la direzione per ogni parametro nella matrice. La direzione di ogni parametro è determinata in uno dei due modi: per impostazione predefinita (per i parametri di input) o tramite **SQLSRV_PARAM _\***  costanti (per i parametri di output e bidirezionali). Ad esempio, il codice seguente specifica il parametro *$employeeId* come parametro di input e il parametro *$usedVacationHours* come parametro bidirezionale:  
  
    ```  
    $params = array(  
                     array($employeeId, SQLSRV_PARAM_IN),  
                     array($usedVacationHours, SQLSRV_PARAM_INOUT)  
                    );  
    ```  
  
    Per comprendere la sintassi per la specifica della direzione dei parametri, si supponga che *$var1*, *$var2*e *$var3* corrispondano rispettivamente ai parametri di input, output e bidirezionale. È possibile specificare la direzione del parametro in uno dei modi seguenti:  
  
    -   Specificare in modo implicito il parametro di input, specificare in modo esplicito il parametro di output e specificare in modo esplicito un parametro bidirezionale:  
  
        ```  
        array(   
               array($var1),  
               array($var2, SQLSRV_PARAM_OUT),  
               array($var3, SQLSRV_PARAM_INOUT)  
               );  
        ```  
  
    -   Specificare in modo esplicito il parametro di input, specificare in modo esplicito il parametro di output e specificare in modo esplicito un parametro bidirezionale:  
  
        ```  
        array(   
               array($var1, SQLSRV_PARAM_IN),  
               array($var2, SQLSRV_PARAM_OUT),  
               array($var3, SQLSRV_PARAM_INOUT)  
               );  
        ```  
  
4.  Eseguire la query con [sqlsrv_query](../../connect/php/sqlsrv-query.md) o con [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) e [sqlsrv_execute](../../connect/php/sqlsrv-execute.md). Ad esempio, il codice seguente usa la connessione *$conn* per eseguire la query *$tsql* con i valori di parametro specificati in *$params*:  
  
    ```  
    sqlsrv_query($conn, $tsql, $params);  
    ```  
  
## <a name="see-also"></a>Vedere anche  
[Procedura: Recuperare i parametri di output mediante il driver SQLSRV](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)

[How to: Retrieve Input and Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver.md)  
  
