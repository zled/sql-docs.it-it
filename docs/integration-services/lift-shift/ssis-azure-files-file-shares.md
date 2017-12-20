---
title: Archiviare e recuperare file nelle condivisioni file in locale e in Azure | Microsoft Docs
description: In questo articolo viene descritto come usare il file system e le condivisioni file, sia a livello locale che in Azure, con SSIS
ms.date: 11/27/2017
ms.topic: article
ms.prod: sql-non-specified
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b6034787f2e6ab34e583c06d219d7415c82d055
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="store-and-retrieve-files-on-file-shares-on-premises-and-in-azure-with-ssis"></a>Archiviare e recuperare file nelle condivisioni file in locale e in Azure con SSIS
In questo articolo viene descritto come aggiornare i pacchetti di SQL Server Integration Services (SSIS) quando si esegue la migrazione lift-and-shift dei pacchetti che usano i file system locali in SSIS in Azure.

> [!IMPORTANT]
> Attualmente il database del catalogo SSIS (SSISDB) supporta solo un singolo set di credenziali di accesso. Di conseguenza, il runtime di integrazione SSIS di Azure non è in grado di usare credenziali diverse per connettersi a più condivisioni file locali e alle condivisioni di File di Azure.

## <a name="store-temporary-files"></a>Archiviare i file temporanei
Se è necessario archiviare ed elaborare i file temporanei durante l'esecuzione di un singolo pacchetto, i pacchetti possono usare la directory di lavoro corrente (`.`) o la cartella temporanea (`%TEMP%`) dei nodi del runtime di integrazione SSIS di Azure.

## <a name="store-files-across-multiple-package-executions"></a>Archiviare i file in più esecuzioni del pacchetto
Se è necessario archiviare ed elaborare i file permanenti e renderli persistenti in più esecuzioni dei pacchetti, è possibile usare condivisioni di file in locale o File di Azure

### <a name="use-on-premises-file-shares"></a>Usare condivisioni di file in locale
Per continuare a usare **condivisioni file locali** quando si spostano pacchetti che usano i file system locali in SSIS in Azure, effettuare le operazioni seguenti:
1.  Trasferire i file dai file system locali alle condivisioni file locali.
2.  Aggiungere le condivisioni file locali a una rete virtuale di Azure.
3.  Aggiungere il runtime di integrazione SSIS di Azure alla stessa rete virtuale. Per altre informazioni, vedere [Aggiungere un runtime di integrazione SSIS di Azure a una rete virtuale](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
4.  Connettere il runtime di integrazione SSIS di Azure alle condivisioni file locali all'interno della stessa rete virtuale impostando le credenziali di accesso che usano l'autenticazione di Windows. Per altre informazioni, vedere [Connettersi a origini dati locali con autenticazione di Windows](ssis-azure-connect-with-windows-auth.md).
5.  Aggiornare i percorsi di file locali nei pacchetti in base ai percorsi UNC che puntano alle condivisioni file locali. Ad esempio, aggiornare `C:\abc.txt` a `\\<on-prem-server-name>\<share-name>\abc.txt`.

### <a name="use-azure-file-shares"></a>Usare le condivisione file di Azure
Per usare **File di Azure** quando si spostano pacchetti che usano i file system locali in SSIS in Azure, effettuare le operazioni seguenti:
1.  Trasferire i file dai file system locali a File di Azure. Per altre informazioni, vedere [File di Azure](https://azure.microsoft.com/services/storage/files/).
2.  Connettere il runtime di integrazione SSIS di Azure a File di Azure impostando le credenziali di accesso che usano l'autenticazione di Windows. Per altre informazioni, vedere [Connettersi a origini dati locali con autenticazione di Windows](ssis-azure-connect-with-windows-auth.md).
3.  Aggiornare i percorsi di file locali nei pacchetti in base ai percorsi UNC che puntano a File di Azure. Ad esempio, aggiornare `C:\abc.txt` a `\\<storage-account-name>.file.core.windows.net\<share-name>\abc.txt`.
