---
title: Provisioning di un Server SQL Linux VM in Azure | Documenti Microsoft
description: In questa esercitazione viene illustrato come creare una macchina virtuale Linux SQL Server 2017 in Azure.
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 222e23b2-51e7-429b-b8e5-61e0ebe7df9b
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 0470622b0fe5a8835213617a4fc2e8c74f674873
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-linux-sql-server-2017-virtual-machine-with-the-azure-portal"></a>Creare una macchina virtuale Linux SQL Server 2017 nel portale di Azure

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

Azure offre immagini di macchina virtuale di Linux che hanno installato SQL Server 2017 RC2. In questo argomento fornisce una breve procedura su come utilizzare il portale di Azure per creare una macchina virtuale Linux SQL Server. 

## <a name="create-a-linux-vm-with-sql-server-installed"></a>Creare una VM Linux con installato SQL Server

Aprire il [portale di Azure](https://portal.azure.com/).

1. Fare clic su **New** a sinistra.

1. Nel **New** pannello, fare clic su **calcolo**.

1. Fare clic su **vedere tutti** accanto al **App in primo piano** intestazione.

   ![Vedere tutte le immagini di macchina virtuale](./media/sql-server-linux-azure-virtual-machine/azure-compute-blade.png)

1. Nella casella di ricerca, digitare **SQL Server 2017**e premere **invio** per avviare la ricerca.

    ![Filtro di ricerca per le immagini di macchina virtuale di SQL Server 2017](./media/sql-server-linux-azure-virtual-machine/searchfilter.png)

    > [!TIP]
    > Questo filtro mostra le immagini di macchina virtuale Linux disponibile per SQL Server 2017. Nel corso del tempo, verranno elencate le immagini di SQL Server 2017 per altre distribuzioni Linux supportate. È anche possibile scegliere questo [collegamento](https://ms.portal.azure.com/#blade/Microsoft_Azure_Marketplace/GalleryFeaturedMenuItemBlade/selectedMenuItemId/home/searchQuery/sql%20server%202017) per passare direttamente ai risultati della ricerca per SQL Server 2017. 

1. Selezionare un'immagine di SQL Server 2017 dai risultati della ricerca.

1. Fare clic su **Crea**.

1. Nel **nozioni di base** pannello, compilare i dettagli per le VM Linux. 

    ![Pannello nozioni di base](./media/sql-server-linux-azure-virtual-machine/basics.png)

    > [!Note]
    > È possibile scegliere di utilizzando una chiave pubblica SSH o una Password per l'autenticazione. SSH è più sicuro. Per istruzioni su come generare una chiave SSH, vedere [creare SSH chiavi su Mac e Linux per le macchine virtuali Linux in Azure](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-mac-create-ssh-keys). 

1. Scegliere **OK**.

1. Nel **dimensioni** pannello, scegliere una dimensione della macchina. Per lo sviluppo e test funzionale, si consiglia una dimensione della macchina virtuale **DS2** o versione successiva. Test delle prestazioni, utilizzare **DS13** o versione successiva.

    ![Scegliere una dimensione di macchina virtuale](./media/sql-server-linux-azure-virtual-machine/vmsizes.png)

    Per visualizzare le altre dimensioni, selezionare **visualizzare tutti**. Per ulteriori informazioni sulle dimensioni della macchina VM, vedere [le dimensioni di VM Linux](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-sizes).

1. Fare clic su **Seleziona**.

1. Nel **impostazioni** pannello, è possibile apportare modifiche alle impostazioni o mantenere le impostazioni predefinite.

1. Scegliere **OK**.

1. Nel **riepilogo** pagina, fare clic su **OK** per creare la macchina virtuale.

> [!NOTE]
> Pre-macchina virtuale di Azure consente di configurare il firewall per aprire la porta di SQL Server 1433 per le connessioni remote. Ma per connettersi in remoto, è necessario anche aggiungere una regola gruppo di sicurezza di rete, come descritto nella sezione successiva.

## <a id="remote"></a>Configurare per le connessioni remote

Per essere in grado di connettersi in remoto a SQL Server in una macchina virtuale di Azure, è necessario configurare una regola in ingresso nel gruppo di sicurezza di rete. La regola consente il traffico sulla porta in cui SQL Server è in ascolto (valore predefinito 1433). La procedura seguente viene illustrato come utilizzare il portale di Azure per questo passaggio. 

1. Nel portale selezionare **macchine virtuali**, quindi selezionare la macchina virtuale di SQL Server.

1. Nell'elenco delle proprietà, selezionare **interfacce di rete**.

1. Selezionare quindi l'interfaccia di rete per la macchina virtuale.

    ![Interfacce di rete](./media/sql-server-linux-azure-virtual-machine/networkinterfaces.png)

1. Scegliere il collegamento di gruppo di sicurezza di rete.

    ![Gruppo di sicurezza di rete](./media/sql-server-linux-azure-virtual-machine/networksecuritygroup.png)

1. Nelle proprietà del gruppo di sicurezza di rete, seleziona **sicurezza regole connessioni in entrata**.

1. Fare clic su di **+ Aggiungi** pulsante.

1. Specificare un nome di "SQLServerRemoteConnections".

1. Nel **servizio** elenco, selezionare **MS SQL**.

    ![Regola gruppo di sicurezza MS SQL](./media/sql-server-linux-azure-virtual-machine/sqlnsgrule.png)

1. Fare clic su **OK** per salvare la regola per la macchina virtuale.

## <a id="connect"></a>Connettersi alla macchina virtuale Linux

Se si utilizza già una shell BASH, connettersi alla macchina virtuale di Azure con il **ssh** comando. Il comando seguente, sostituire il nome utente della macchina virtuale e l'indirizzo IP per la connessione per le VM Linux.

```bash
ssh -l AzureAdmin 100.55.555.555
```

È possibile trovare l'indirizzo IP della macchina virtuale nel portale di Azure.

![Indirizzo IP nel portale di Azure](./media/sql-server-linux-azure-virtual-machine/vmproperties.png)

Se in esecuzione in Windows e non è una shell BASH, è possibile installare un client SSH, ad esempio PuTTY.

1. [Scaricare e installare PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

1. Eseguire PuTTY.

1. Nella schermata di configurazione di PuTTY immettere l'indirizzo IP pubblico della macchina virtuale.

1. Fare clic su Apri e immettere il nome utente e password quando richiesti.

Per ulteriori informazioni sulla connessione alle macchine virtuali Linux, vedere [creare una VM Linux in Azure tramite il portale](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-quick-create-portal#ssh-to-the-vm).

## <a name="configure-sql-server"></a>Configurare SQL Server

1. Dopo la connessione a VM Linux, aprire un nuovo comando terminal.

1. Configurare SQL Server con il comando seguente.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup 
   ```

   Accettare le condizioni di licenza e immettere una password per l'account di amministratore di sistema. È possibile avviare il server quando richiesto.

1. Facoltativamente, [installare gli strumenti di SQL Server](sql-server-linux-setup-tools.md).

## <a name="next-steps"></a>Passaggi successivi

Dopo avere creato una macchina virtuale di SQL Server 2017 in Azure, è possibile connettersi in locale con **sqlcmd** per eseguire query Transact-SQL.

Se è stata configurata la macchina virtuale di Azure per le connessioni remote di SQL Server, inoltre deve essere in grado di connettersi in remoto. Per un esempio di connessione a SQL Server in Linux da un computer remoto di Windows, vedere [utilizzare SQL Server Management Studio in Windows per connettersi a SQL Server in Linux](sql-server-linux-develop-use-ssms.md).

Per ulteriori informazioni generali sulle macchine virtuali Linux in Azure, vedere il [documentazione di macchina virtuale Linux](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/).

