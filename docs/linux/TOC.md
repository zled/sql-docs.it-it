# [Informazioni su SQL Server in Linux](sql-server-linux-overview.md)

# Panoramica
## [Note sulla versione](sql-server-linux-release-notes.md)
## [Novità in questa versione](sql-server-linux-whats-new.md)
## [Articoli nuovi e aggiornati](new-updated-linux.md)
## [Edizioni e funzionalità supportate ](sql-server-linux-editions-and-components-2017.md)

# Guide introduttive
## [Installazione e connessione - Red Hat](quickstart-install-connect-red-hat.md)
## [Installazione e connessione - SUSE](quickstart-install-connect-suse.md)
## [Installazione e connessione - Ubuntu](quickstart-install-connect-ubuntu.md)
## [Esecuzione e connessione - Docker](quickstart-install-connect-docker.md)
## [Eseguire il provisioning di una macchina virtuale SQL in Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)
## [Esecuzione e connessione - Cloud](quickstart-install-connect-clouds.md)

# Esercitazioni
## [Eseguire la migrazione da Windows](sql-server-linux-migrate-restore-database.md)
## [Eseguire la migrazione da Oracle](../ssma/oracle/sql-server-linux-convert-from-oracle.md?toc=%2fsql%2flinux%2ftoc.json)
## [Eseguire la migrazione da Docker](tutorial-restore-backup-in-sql-server-container.md)
## [Creare un processo](sql-server-linux-run-sql-server-agent-job.md)
## [Configurare l'autenticazione di AD](sql-server-linux-active-directory-authentication.md)
## [Creare l'istanza del cluster di failover](sql-server-linux-shared-disk-cluster-configure.md)
### [iSCSI](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
### [NFS](sql-server-linux-shared-disk-cluster-configure-nfs.md)
### [SMB](sql-server-linux-shared-disk-cluster-configure-smb.md)

# Concetti
## Install
### [Installare SQL Server](sql-server-linux-setup.md)
### [Installare SQL Server Data Tools](sql-server-linux-setup-tools.md)
### [Installare SQL Server Agent](sql-server-linux-setup-sql-agent.md)
### [Installare la ricerca full-text di SQL Server](sql-server-linux-setup-full-text-search.md)
### [Installare SQL Server Integration Services](sql-server-linux-setup-ssis.md)
### [Registrare il repository GA](sql-server-linux-change-repo.md)

## Configura
### [Configurare con mssql-conf](sql-server-linux-configure-mssql-conf.md)
### [Variabili di ambiente](sql-server-linux-configure-environment-variables.md)
### [Configurare i contenitori di Docker](sql-server-linux-configure-docker.md)
### [Commenti e suggerimenti degli utenti](sql-server-linux-customer-feedback.md)

## [Sviluppo](sql-server-linux-develop-overview.md)
### [Librerie di connettività](sql-server-linux-develop-connectivity-libraries.md)
### [Usare Visual Studio Code](sql-server-linux-develop-use-vscode.md)
### [Usare SSMS](sql-server-linux-develop-use-ssms.md)
### [Usare SSDT](sql-server-linux-develop-use-ssdt.md)

## [Gestire](sql-server-linux-management-overview.md)
### [Usare SSMS per la gestione](sql-server-linux-manage-ssms.md)
### [Usare PowerShell per la gestione](sql-server-linux-manage-powershell.md)
### [Usare il log shipping](sql-server-linux-use-log-shipping.md)
### [Usare gli avvisi di posta elettronica e Posta elettronica database](sql-server-linux-db-mail-sql-agent.md)

## [Migrazione](sql-server-linux-migrate-overview.md)
### [Esportare e importare un file BACPAC in Windows](sql-server-linux-migrate-ssms.md)
### [Eseguire la migrazione con SQL Server Migration Assistant](sql-server-linux-migrate-ssma.md)
### [Eseguire la copia bulk con bcp](sql-server-linux-migrate-bcp.md)

## [Estrarre, trasformare, caricare](sql-server-linux-migrate-ssis.md)
### [Limitazioni e problemi noti](sql-server-linux-ssis-known-issues.md)
### [Configura SSIS](sql-server-linux-configure-ssis.md)
### [Pianificare i pacchetti SSIS](sql-server-linux-schedule-ssis-packages.md)

## [Configurare la continuità aziendale](sql-server-linux-business-continuity-dr.md)
### [Backup e ripristino](sql-server-linux-backup-and-restore-database.md)
#### [Interfaccia dispositivo virtuale - Linux](sql-server-linux-backup-vdi-specification.md)
### [Istanza del cluster di failover](sql-server-linux-shared-disk-cluster-concepts.md)
#### [Red Hat Enterprise Linux]()
##### [Configurare High Availability Add-On](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)
##### [Gestire High Availability Add-On](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
#### [SUSE Linux Enterprise Server]()
##### [Configurare High Availability Add-On](sql-server-linux-shared-disk-cluster-sles-configure.md)
### [Gruppi di disponibilità](sql-server-linux-availability-group-overview.md)
#### [Impostare la disponibilità elevata](sql-server-linux-availability-group-ha.md)
##### [Configurare AG](sql-server-linux-availability-group-configure-ha.md)
##### [Configurare su RHEL](sql-server-linux-availability-group-cluster-rhel.md)
##### [Configurare su SUSE](sql-server-linux-availability-group-cluster-sles.md)
##### [Configurare su Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)
##### [Gestire](sql-server-linux-availability-group-failover-ha.md)
#### [Creare solo per la scalabilità in lettura]()
##### [Configurare AG](sql-server-linux-availability-group-configure-rs.md)

## [Sicurezza](sql-server-linux-security-overview.md)
### [Introduzione alle funzionalità di sicurezza](sql-server-linux-security-get-started.md)
### [Crittografia delle connessioni](sql-server-linux-encrypted-connections.md)

## Prestazioni
### [Procedure consigliate](sql-server-linux-performance-best-practices.md)
### [Introduzione alle funzionalità relative alle prestazioni](sql-server-linux-performance-get-started.md)

# Esempi
## Installazione automatica
### [Red Hat Enterprise Linux](sample-unattended-install-redhat.md)
### [SUSE Linux Enterprise Server](sample-unattended-install-suse.md)
### [Ubuntu](sample-unattended-install-ubuntu.md)

# Risorse
## [Risoluzione dei problemi](sql-server-linux-troubleshooting-guide.md)
## [Documentazione di SQL Server](../sql-server/sql-server-technical-documentation.md)
## Partner
### [Monitoraggio](../sql-server/partner-monitor-sql-server.md)
### [Disponibilità elevata e ripristino di emergenza](../sql-server/partner-hadr-sql-server.md)
### [Gestione](../sql-server/partner-management-sql-server.md)
### [Sviluppo](../sql-server/partner-dev-sql-server.md)
## [DBA Stack Exchange](https://dba.stackexchange.com/questions/tagged/sql-server)
## [Stack Overflow](http://stackoverflow.com/questions/tagged/sql-server)
## [Forum di MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
## [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback)
## [Reddit](https://www.reddit.com/r/SQLServer)
