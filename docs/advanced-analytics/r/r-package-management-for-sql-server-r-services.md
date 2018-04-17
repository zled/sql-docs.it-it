---
title: Installare e gestire pacchetti di machine learning in SQL Server | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: cbab4687dd0d5a8cb250fa38fc4c4c7dbb9d68a6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="install-and-manage-machine-learning-packages-in-sql-server"></a>Installare e gestire pacchetti di machine learning in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene descritto come installare nuovi pacchetti R o Python in SQL Server 2017 e in SQL Server 2016. Vengono inoltre descritte le limitazioni per i pacchetti che è possibile installare in SQL Server.

## <a name="overview-of-package-management-methods-and-requirements"></a>Panoramica dei requisiti e i metodi di gestione dei pacchetti

A differenza di sviluppo R o Python tipico, i pacchetti utilizzati da SQL Server devono essere installati in una cartella sotto il controllo amministrativo. Esistono numerosi vantaggi per mantenere i pacchetti in un'unica posizione:

+ L'amministratore del server è possibile monitorare l'aggiunta di nuovi file e le librerie nel server e controllare l'aumento delle dimensioni dei file utilizzati dalle librerie di pacchetto. 
+ Pacchetti possono essere più facilmente condiviso da più utenti di database, anziché l'installazione di più copie dello stesso pacchetto in librerie utente.
+ Possono essere installati solo i pacchetti protetti, approvati, per proteggere il server e le relative operazioni.

Tuttavia, queste restrizioni necessariamente alcune modifiche in modo che gli esperti di dati e gli analisti di lavoro:

+ In genere, è necessario l'accesso amministrativo al server. In SQL Server 2017, l'amministratore del database può utilizzare i ruoli per consentire a determinati utenti di installare i pacchetti per l'uso privato, ma l'amministratore deve abilitare questa funzionalità.
+ Numero di server non dispone dell'accesso a Internet. L'installazione di pacchetti a tali computer richiede alcune attività di preparazione aggiuntive.
+ I pacchetti vengono installati in una libreria di istanza. Pacchetti non possono essere condivisa tra più istanze.
+ Gli utenti non è possibile eseguire i pacchetti che sono stato installato in una libreria di utente.

## <a name="package-installation-guides-for-r-or-python"></a>Guide all'installazione di pacchetti di R o Python

Vedere gli articoli seguenti per informazioni dettagliate su come installare i nuovi pacchetti R o Python. 

### <a name="install-new-r-packages"></a>Installare i nuovi pacchetti R

+ [Installare pacchetti R aggiuntivi su SQL Server](install-additional-r-packages-on-sql-server.md)

    È possibile installare pacchetti R in SQL Server 2016 o 2017 come amministratore, utilizzando gli strumenti di R.

    È inoltre possibile installare pacchetti R da un client remoto di R in R Server 9.0.2 o versione successiva è installato.

    È anche possibile installare pacchetti R in SQL Server 2017 utilizzando le istruzioni DDL.

### <a name="install-new-python-packages"></a>Installare i nuovi pacchetti di Python

+ [Installare nuovi pacchetti Python in SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="prerequisites"></a>Prerequisiti

Prima di tentare di scaricare o installare qualsiasi nuovo pacchetto, esaminare i requisiti:

+ Assicurarsi che vi sia una versione del pacchetto di Windows: [ottenere la versione corretta del pacchetto e il formato](#packageVersion)

+ Identificare tutte le dipendenze di pacchetto e verificare la compatibilità con l'ambiente di SQL Server.

+ Verificare la versione di R o la compatibilità delle versioni Python. Il pacchetto deve essere compatibile con la versione di R o Python che è in esecuzione in SQL Server.

+ Autorizzazioni. Determinare se si dispone di diritti per installare il pacchetto. Per installare la libreria di istanza, è necessario l'accesso amministrativo al computer che esegue SQL Server. Se non si dispone di accesso amministrativo al computer SQL Server, è possibile trovare un amministratore del database per l'installazione del pacchetto.

    In SQL Server 2017, è possibile installare pacchetti R da un client remoto, se abilitata nel server di gestione dei pacchetti e si è proprietario del database o membro di un ruolo di gestione del pacchetto.

+ Prendere in considerazione i rischi e i vantaggi derivanti dall'installazione di un particolare pacchetto nell'ambiente di SQL Server. Controllare se il pacchetto (o tutti i pacchetti che richiede) include funzionalità che verranno bloccate da SQL Server o da criteri. Numero di pacchetti R e Python è una scarsa adatta per un ambiente protezione avanzato di SQL Server. Problemi possono includere:

    - Pacchetti che accedono alla rete
    - Pacchetti che richiedono Java o altri Framework non è in genere utilizzato in un ambiente di SQL Server
    - Pacchetti che richiedono l'accesso con privilegi elevati di file system
    - Pacchetto viene utilizzato per lo sviluppo web o altre attività che non traggono vantaggio dall'esecuzione all'interno di SQL Server.

## <a name="installation-on-servers-with-no-internet-access"></a>Installazione in un server senza accesso a Internet

In generale, i server che ospitano i database di produzione consentono la connessione a Internet. L'installazione di nuovi pacchetti R o Python in tali ambienti è necessario preparare in anticipo tutti i pacchetti e le relative dipendenze e copiare i file in una cartella sul server per l'utilizzo nell'installazione.

1. Identificare tutte le dipendenze di pacchetto. 
2. Verificare se tutti i pacchetti necessari sono già installati nel server. Se il pacchetto è installato, verificare che la versione sia corretta.
3. Scaricare il pacchetto e tutte le dipendenze in un computer separato.
4. Spostare i file in una cartella accessibile dal server.
5. Eseguire un comando di installazione supportati o l'istruzione DDL per installare il pacchetto nella libreria di istanza.

Identificare tutte le dipendenze può essere complicato. Per R, è consigliabile utilizzare [miniCRAN](create-a-local-package-repository-using-minicran.md) per preparare un repository di pacchetti non in linea.

Per Python, è necessario preparare tutte le dipendenze in modo analogo e salvarli localmente. Assicurarsi di utilizzare un file binari compatibili con Windows e utilizzare il formato WHL.
