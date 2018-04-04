---
title: Informazioni sugli esempi di codice nella documentazione di | Documenti Microsoft
ms.custom: ''
ms.date: 03/26/2018
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
ms.assetid: 3f035c37-0f2e-47d4-94e0-a10774402e82
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a5515db3c5b98ddb0c3645016eade20ecf4f224b
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="about-code-examples-in-the-documentation"></a>Informazioni sugli esempi di codice nella documentazione
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="remarks-about-the-code-examples"></a>Sezione Osservazioni sugli esempi di codice
Esistono diversi aspetti da tenere presenti durante l'esecuzione degli esempi di codice presenti nella documentazione di [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] :  
  
-   Quasi tutti gli esempi si presuppongono che SQL Server 2008 o versione successiva e il database AdventureWorks siano installati nel computer locale.  
  
    Per informazioni su come scaricare versioni gratuite e versioni di valutazione di SQL Server, vedere [SQL Server](http://go.microsoft.com/fwlink/?LinkID=120193).  
  
    Per informazioni su come scaricare e installare il database AdventureWorks, vedere la [pagina AdventureWorks nel repository Github degli esempi di SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works).
  
-   Quasi tutti gli esempi di codice di questa documentazione sono destinati a essere eseguiti dalla riga di comando, che consente il test automatizzato di tutti gli esempi di codice. Per informazioni sull'esecuzione di PHP dalla riga di comando, vedere [Utilizzo PHP da linea di comando](http://php.net/manual/en/features.commandline.php).  
  
-   Sebbene gli esempi sono progettati per essere eseguiti dalla riga di comando, è possibile eseguire ogni esempio tramite chiamata da un browser senza apportare modifiche allo script. Per formattare correttamente l'output, sostituire ogni "\n" con "\<\/br >" in ogni esempio prima di richiamare da un browser.  
  
-   Allo scopo di mantenere ogni esempio mirato, non è stata eseguita una gestione degli errori corretta in tutti gli esempi. Si consiglia, pertanto, di ricercare eventuali errori in tutte le chiamate a una funzione **sqlsrv** o a un metodo PDO e di gestirli in base alle esigenze dell'applicazione.  
  
    Un modo semplice per ottenere informazioni sugli errori quando si verifica un errore consiste nel chiudere lo script con la riga di codice seguente:  
  
    ```  
    die( print_r( sqlsrv_errors(), true));  
    ```  
  
    Oppure, se si usa PDO,  
  
    ```  
    print_r ($stmt->errorInfo());  
    die();  
    ```  
  
    Per altre informazioni sulla gestione di errori e avvisi, vedere l'articolo relativo alla [gestione di errori e avvisi](../../connect/php/handling-errors-and-warnings.md).  
  
## <a name="see-also"></a>Vedere anche  
[Panoramica dei driver Microsoft per PHP per SQL Server](../../connect/php/overview-of-the-php-sql-driver.md)
  
