### <a id="sampledata"></a> Caricare dati di esempio

Esercitazioni di cluster di SQL Server i big data usano un set comune di dati di esempio. Usare la procedura seguente per configurare i dati di esempio nel cluster di big data:

1. Se non si è gli strumenti da riga di comando di SQL Server (**sqlcmd** e **bcp**), prima di tutto installare questi strumenti con uno dei collegamenti:

   * **Windows**: [gli strumenti da riga di comando di installazione di SQL Server in Windows](https://www.microsoft.com/download/details.aspx?id=53591)
   * **Linux**: [gli strumenti da riga di comando di installazione di SQL Server in Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-tools)

1. Scaricare il file di backup di esempio [tpcxbb_1gb.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak) nel computer.

1. Passare al cluster di big data di SQL Server 2019 [directory degli esempi](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster).

1. Scaricare il [bootstrap-esempio-db.sql](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql) script Transact-SQL.

1. Scaricare ed eseguire uno degli script di due esempio seguenti dalla riga di comando:

   * **Windows**: [bootstrap-esempio-db.cmd](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd)
   * **Linux**: [bootstrap-esempio-db.sh](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh)

   > [!TIP]
   > È possibile ottenere istruzioni sull'utilizzo eseguendo lo script senza parametri.

Lo script Ripristina il database di esempio per l'istanza master di SQL Server e carica anche i dati in HDFS nel pool di archiviazione.