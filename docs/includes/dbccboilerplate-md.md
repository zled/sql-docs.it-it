Cercare l'errore hardware. Eseguire gli strumenti di diagnostica hardware e risolvere eventuali problemi. Esaminare inoltre i registri applicazioni e il Registro di sistema di Windows, nonché il log degli errori di SQL Server per stabilire se l'errore è dovuto a un problema hardware. Risolvere tutti i problemi relativi all'hardware indicati nei log.

In caso di problemi persistenti che provocano il danneggiamento dei dati, provare a sostituire i vari componenti hardware per isolare il problema. Verificare che nel sistema non sia abilitata la memorizzazione nella cache in scrittura sul controller del disco. Se si ritiene che il problema sia dovuto alla memorizzazione nella cache in scrittura, rivolgersi al fornitore dell'hardware.

Infine, potrebbe essere conveniente passare a un nuovo sistema hardware. A tale scopo può essere necessario riformattare le unità disco e reinstallare il sistema operativo.

Ripristino da un backup. Se il problema non è correlato all'hardware ed è disponibile un backup valido noto, ripristinare il database dal backup.

Eseguire DBCC CHECKDB. Se non è disponibile un backup valido, eseguire DBCC CHECKDB senza la clausola REPAIR per determinare l'entità del danno. Verrà automaticamente suggerita la clausola REPAIR da usare. Eseguire quindi DBCC CHECKDB con la clausola REPAIR appropriata per correggere il database.

> **alert tag is not supported!!!!**
> **tr tag is not supported!!!!**
> **tr tag is not supported!!!!**

Se l'esecuzione di DBCC CHECKDB con una clausola REPAIR non consente di risolvere il problema, contattare il personale del supporto tecnico.

