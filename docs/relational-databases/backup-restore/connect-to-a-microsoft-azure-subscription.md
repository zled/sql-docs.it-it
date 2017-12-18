---
title: Connettersi a una sottoscrizione di Microsoft Azure | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: backup-restore
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cca5a270-643f-4677-8802-98464f19f82a
caps.latest.revision: "4"
author: dagiro
ms.author: v-dagir
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4a014146048e59e437167b340dc34e3be64d0665
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="connect-to-a-microsoft-azure-subscription"></a>Connettersi a una sottoscrizione di Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Usare **Connetti a una sottoscrizione Microsoft** per registrare un contenitore BLOB di Azure esistente con l'istanza di SQL Server.  Nella finestra di dialogo verrà creata una firma di accesso condiviso e un criterio di accesso condiviso in un contenitore BLOB di Azure, quindi verranno create le credenziali di SQL Server.  Questa finestra di dialogo viene visualizzata quando si usa l'attività Backup o Ripristina di SQL Server Management Studio e l'operazione implica un dispositivo URL.

## <a name="limitation"></a>Limitazione
**Connettersi a una sottoscrizione di Microsoft Azure** funzionerà solo con un account di archiviazione di Microsoft Azure creato tramite il modello di distribuzione di Gestione dei servizi (classica).  Per altre informazioni sui modelli di distribuzione di Microsoft Azure, vedere [Confronto tra distribuzione di Azure Resource Manager e classica](https://azure.microsoft.com/en-us/documentation/articles/resource-manager-deployment-model/).

## <a name="options"></a>Opzioni
**Accedi**     
Accedere con l'account Azure appropriato.

**Selezionare la sottoscrizione da usare**      
Selezionare la sottoscrizione desiderata dall'elenco a discesa.

**Selezionare l'account di archiviazione**  
Selezionare l'account di archiviazione desiderato dall'elenco a discesa.

**Selezionare il contenitore BLOB**   
Selezionare il contenitore BLOB desiderato dall'elenco a discesa.

**Scadenza criteri di accesso condiviso**   
I criteri di accesso condiviso scadranno alla data indicata.  La data di scadenza predefinita è un anno dalla creazione.  Modificare come desiderato.

**Firma di accesso condiviso generata**   
Nella casella di testo con formattazione verrà visualizzata la firma di accesso condiviso creata.

**Crea credenziali**   
Il pulsante genererà i criteri di accesso condiviso e una firma di accesso condiviso, quindi creerà le credenziali di SQL Server.
