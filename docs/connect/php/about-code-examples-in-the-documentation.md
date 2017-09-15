---
title: Informazioni sugli esempi di codice nella documentazione di | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f035c37-0f2e-47d4-94e0-a10774402e82
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d24d29aba9db9d3626a456f87f799e00da1b42cc
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="about-code-examples-in-the-documentation"></a>Informazioni sugli esempi di codice nella documentazione
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Esistono diversi aspetti da tenere presenti durante l'esecuzione degli esempi di codice presenti nella documentazione di [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] :  
  
-   In quasi tutti gli esempi si presuppone che SQL Server 2005 o versione successiva (SQL Server 2008 o versione successiva se si usa la versione 3.1) e il database AdventureWorks siano installati nel computer locale.  
  
    Per informazioni su come scaricare versioni gratuite e versioni di valutazione di SQL Server, vedere [SQL Server](http://go.microsoft.com/fwlink/?LinkID=120193).  
  
    Per informazioni su come scaricare il database AdventureWorks, vedere l'articolo relativo a [esempi per Microsoft SQL Server e progetti della community](http://go.microsoft.com/fwlink/?LinkID=67739).  
  
    Per altre informazioni su come installare il database AdventureWorks, vedere la [procedura dettagliata per l'installazione del database AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=65819).  
  
-   Quasi tutti gli esempi di codice di questa documentazione sono destinati a essere eseguiti dalla riga di comando, che consente il test automatizzato di tutti gli esempi di codice. Per informazioni sull'esecuzione di PHP dalla riga di comando, vedere [Utilizzo PHP da linea di comando](http://php.net/manual/en/features.commandline.php).  
  
-   Sebbene gli esempi siano scritti per essere eseguiti dalla riga di comando, è possibile eseguire ogni esempio tramite chiamata da un browser senza apportare modifiche allo script. Per ottenere una formattazione piacevole dell'output, sostituire ogni "\n" con "\<\/br >" in ogni esempio prima della chiamata da un browser.  
  
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
[Panoramica del driver SQL PHP](../../connect/php/overview-of-the-php-sql-driver.md)
  

