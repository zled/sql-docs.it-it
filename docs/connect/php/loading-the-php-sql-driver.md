---
title: Caricamento del Driver SQL PHP | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: loading the driver
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
caps.latest.revision: "42"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 90ba63857ea38481577083d2a85999e789dfcb84
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="loading-the-php-sql-driver"></a>Caricamento del driver SQL PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento vengono fornite le istruzioni per il caricamento dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] nello spazio di elaborazione PHP.  
  
Sono disponibili due opzioni per il caricamento di un driver. Il driver può essere caricato all'avvio di PHP o in fase di esecuzione dello script PHP.  
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Spostamento del file del driver nella directory dell'estensione  
Indipendentemente dalla procedura usata, il primo passaggio sarà quello di inserire il file del driver in una directory in cui può essere individuato durante l'esecuzione PHP. Inserire il file del driver nella directory dell'estensione PHP. Vedere [Requisiti di sistema per il driver SQL PHP](../../connect/php/system-requirements-for-the-php-sql-driver.md) per un elenco dei file dei driver installati con i [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
Se necessario, specificare il percorso della directory del file del driver nel file di configurazione PHP (php.ini) usando il **extension_dir** opzione. Ad esempio, se il file del driver viene inserito nella directory c:\php\ext directory, usare questa opzione:  
  
```  
extension_dir = "c:\PHP\ext"  
```  
  
## <a name="loading-the-driver-at-php-startup"></a>Caricamento del driver all'avvio di PHP  
Per caricare i [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] all'avvio di PHP, spostare innanzitutto un file di driver nella directory dell'estensione. Quindi eseguire la procedura seguente:  
  
1.  Per abilitare il **SQLSRV** driver, modificare **php.ini** aggiungendo la riga seguente alla sezione dell'estensione o modificando la riga è già presente:  
  
    In Windows (in questo esempio Usa il driver thread-safe versione 4.0 per PHP 7): 
    ```  
    extension=php_sqlsrv_7_ts.dll  
    ```  
    In Linux (in questo esempio Usa la versione installati da PECL): 
    ```  
    extension=sqlsrv.so  
    ```  
    Per abilitare il **PDO_SQLSRV** driver, modificare **php.ini** aggiungendo la riga seguente alla sezione dell'estensione o modificando la riga è già presente:  
  
    In Windows (in questo esempio Usa il driver thread-safe versione 4.0 per PHP 7):
    ```  
    extension=php_pdo_sqlsrv_7_ts.dll  
    ```  
    In Linux (in questo esempio Usa la versione installati da PECL):
    ```  
    extension=pdo_sqlsrv.so  
    ```  
  
2.  Se si desidera utilizzare il **PDO_SQLSRV** driver, l'estensione di oggetti dati PHP (PDO) deve essere disponibile come estensione incorporata o come estensione a caricamento dinamico. Se è necessario caricare il driver PDO_SQLSRV in modo dinamico, il file php_pdo.dll (o pdo.so in Linux) deve essere presente nella directory dell'estensione e la riga seguente deve essere nel file php.ini:

    In Windows:  
    ```
    extension=php_pdo.dll  
    ```  
    In Linux:  
    ```
    extension=pdo.so  
    ```  
  
3.  Riavviare il server Web.  
  
> [!NOTE]  
> Per determinare se il driver è stato caricato correttamente, eseguire uno script che chiama [phpinfo](http://go.microsoft.com/fwlink/?LinkId=108678).  
  
Per altre informazioni sui parametri di **php.ini** , vedere [Descrizione dei parametri core di php.ini](http://go.microsoft.com/fwlink/?LinkId=105817).  
  
## <a name="loading-the-driver-at-php-script-runtime"></a>Caricamento del driver durante l'esecuzione dello script PHP  
Per caricare i [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] durante l'esecuzione dello script, spostare innanzitutto un file di driver nella directory dell'estensione. Quindi includere la riga seguente all'inizio dello script PHP che soddisfi il nome del file del driver:  
  
```  
dl('php_pdo_sqlsrv_7_ts.dll');  
```  
  
Per ulteriori informazioni sulle funzioni PHP correlate al caricamento dinamico delle estensioni, vedere [dl](http://go.microsoft.com/fwlink/?LinkId=105818) e [extension_loaded.](http://go.microsoft.com/fwlink/?LinkId=105819)  
  
## <a name="see-also"></a>Vedere anche  
[Introduzione al driver SQL PHP](../../connect/php/getting-started-with-the-php-sql-driver.md)
[Requisiti di sistema per il driver SQL PHP](../../connect/php/system-requirements-for-the-php-sql-driver.md)
[Guida di programmazione per il driver SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  
