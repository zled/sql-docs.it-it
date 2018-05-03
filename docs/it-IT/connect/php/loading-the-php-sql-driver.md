---
title: Caricamento dei driver Microsoft per PHP per SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- loading the driver
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c29424ef266d627e2194a309da54741bc170ae27
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>Caricamento dei Driver Microsoft per PHP per SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Questa pagina vengono fornite istruzioni per il caricamento di [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] nello PHP spazio di elaborazione.  
  
È possibile scaricare i driver predefiniti per la piattaforma nella [Microsoft Drivers for PHP per SQL Server](https://github.com/Microsoft/msphpsql/releases) pagina progetto Github. Ogni pacchetto di installazione contiene file di driver SQLSRV e PDO_SQLSRV in varianti con modello di threading e non a thread singolo. In Windows, sono anche disponibili in varianti a 32 e 64 bit. Vedere [requisiti di sistema per Microsoft Drivers for PHP per SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md) per un elenco dei file di driver che sono contenuti in ogni pacchetto. Il file di driver deve corrispondere la versione PHP, architettura e threadedness dell'ambiente di PHP.

Su Linux e macOS, i driver possono in alternativa essere installati usando PECL, come individuata nel [esercitazione installazione](../../connect/php/installation-tutorial-linux-mac.md).
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Spostamento del file del driver nella directory dell'estensione  
Il file del driver deve trovarsi in una directory in cui il runtime PHP possibile trovarlo. È consigliabile inserire il file di driver nella directory dell'estensione PHP predefiniti, per trovare la directory predefinita, eseguire `php -i | sls extension_dir` in Windows o `php -i | grep extension_dir` su Linux/macOS. Se non si utilizza la directory di estensione predefinito, specificare una directory nel file di configurazione PHP (PHP. ini), utilizzando il **extension_dir** opzione. Ad esempio, in Windows, se è stato inserito il file del driver `c:\php\ext` directory, aggiungere la riga seguente al file PHP. ini:
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>Caricamento del driver all'avvio di PHP  
Per caricare il driver SQLSRV all'avvio di PHP, spostare innanzitutto un file di driver nella directory dell'estensione. Quindi eseguire la procedura seguente:  
  
1.  Per abilitare il **SQLSRV** driver, modificare **PHP. ini** aggiungendo la riga seguente alla sezione dell'estensione, modificare il nome del file come appropriato:  
  
    In Windows: 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    In Linux, se sono stati scaricati i file binari predefiniti per la distribuzione: 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    Se è stato compilato il binario SQLSRV dall'origine o con PECL, verranno invece denominate sqlsrv.so:
    ```
    extension=sqlsrv.so
    ```
  
2.  Per abilitare il **PDO_SQLSRV** driver, l'estensione di oggetti dati PHP (PDO) deve essere disponibile, come estensione incorporata o come estensione caricata in modo dinamico.

    In Windows, i file binari PHP predefiniti forniti con PDO predefinito, in modo da non dover modificare PHP. ini per caricarla. Se, tuttavia, si dispone compilati PHP dall'origine e specificare un'estensione PDO separata da compilare, verranno denominate `php_pdo.dll`, ed è necessario copiarlo nella directory di estensione e aggiungere la riga seguente al file PHP. ini:  
    ```
    extension=php_pdo.dll  
    ```
    In Linux, se è stato installato usando Gestione pacchetti del sistema, PHP PDO probabilmente viene installato come un'estensione caricata in modo dinamico denominata pdo.so. L'estensione PDO deve essere caricato prima dell'estensione PDO_SQLSRV o il caricamento avrà esito negativo. Le estensioni vengono in genere caricate utilizzando file con estensione ini singoli, e questi file vengono lette dopo PHP. ini. Pertanto, se pdo.so viene caricato tramite il proprio file. ini, è necessario un file separato caricamento del driver PDO_SQLSRV dopo PDO. 

    Per trovare la directory si trovano i file con estensione ini specifiche dell'estensione, eseguire `php --ini` e prendere nota della directory indicata in `Scan for additional .ini files in:`. Trovare il file che carica pdo.so: probabilmente è preceduta da un numero, ad esempio 10 pdo.ini. Il prefisso numerico indica l'ordine di caricamento dei file. ini, mentre i file che non contengono un prefisso numerico vengono caricati in ordine alfabetico. Creare un file per caricare il file del driver PDO_SQLSRV chiamato 30-pdo_sqlsrv.ini (qualsiasi numero maggiore di quello che prefissi pdo.ini works) oppure pdo_sqlsrv.ini (se pdo.ini non preceduta da un numero) e aggiungere la riga seguente, modificando il nome del file come appropriato:  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    Come con SQLSRV, se è stato compilato il binario PDO_SQLSRV dall'origine o con PECL, verranno invece denominate pdo_sqlsrv.so:
    ```
    extension=pdo_sqlsrv.so
    ```
    Copiare questo file nella directory che contiene altri file. ini. 

    Se è stato compilato PHP dall'origine con supporto incorporato per PDO, non è necessario un file. ini separato ed è possibile aggiungere la riga appropriata in precedenza per PHP. ini.
  
3.  Riavviare il server Web.  
  
> [!NOTE]  
> Per determinare se il driver è stato caricato correttamente, eseguire uno script che chiama [phpinfo](http://php.net/manual/en/function.phpinfo.php).  
  
Per ulteriori informazioni **PHP. ini** , vedere [descrizione dei core ini](http://php.net/manual/en/ini.core.php).  
  
## <a name="see-also"></a>Vedere anche  
[Guida introduttiva con i driver Microsoft per PHP per SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Requisiti di sistema per i driver Microsoft per PHP per SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)

[Guida di programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Riferimento all'API del Driver PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
