---
title: Introduzione a SQL Server 2017 nel Cloud | Documenti Microsoft
description: Questa esercitazione rapida viene illustrato come eseguire il 2017 di SQL Server in Linux nel cloud di propria scelta.
author: annashres
ms.author: annashres
manager: craigg
ms.date: 10/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.component: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.openlocfilehash: 645c3e11621b1c9faecffc7edf76df9a6a1eabab
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="run-the-sql-server-2017-in-the-cloud"></a>Eseguire il 2017 di SQL Server nel cloud

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questa esercitazione di avvio rapido, verrà installato 2017 di SQL Server su Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) o Ubuntu nel cloud di propria scelta. Passare a [il provisioning di una macchina virtuale Linux SQL Server nel portale di Azure](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json) per l'esecuzione di SQL Server in Linux in Azure.

    > [!NOTE]
    > If you choose to run a paid edition of SQL Server then you need to bring your own license (BYOL)

## <a name="amazon-web-services"></a>Amazon Web Services
1.  Creare un AMI Linux con almeno 2 GB di memoria da marketplace 
    * [RHEL 7.3 +](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES v12 SP2](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  Connettere il AMI con ssh
1.  Seguire la Guida rapida per il distrbution Linux che scelto: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Configurare per le connessioni remote: 
    * Aprire il [EC2 Amazon console]( https://console.aws.amazon.com/ec2/)
    * Nel riquadro di spostamento, scegliere **gruppi di sicurezza**. 
    * Scegliere **in ingresso, modifica, aggiungere una regola**
    * Aggiungere una regola in entrata per consentire il traffico sulla porta in cui SQL Server è in ascolto (porta predefinita TCP 1433)

    
## <a name="digital-ocean"></a>Firma digitale oceano
1. Account di accesso per il [Pannello di controllo](https://cloud.digitalocean.com/login) e fare clic su Crea un droplet
1. Scegliere un droplet Ubuntu 16.04 con almeno 2 GB di memoria
1. Connettere il droplet con ssh
1. Seguire il [delle Guide rapide Ubuntu](quickstart-install-connect-ubuntu.md)
1. Configurare per le connessioni remote:
    * Nella parte superiore del Pannello di controllo, seguire la **rete** collegamento e quindi selezionare **firewall**
    * Aggiungere una regola in entrata per consentire il traffico sulla porta in cui SQL Server è in ascolto (porta predefinita TCP 1433)
    
## <a name="google-cloud-platform"></a>Google Cloud Platform
1.  Creare un'immagine Linux con almeno 2 GB di memoria dall'avvio Cloud 
    * [RHEL 7.3 +](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES v12 SP2](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  Connettersi all'immagine con ssh
1.  Seguire la Guida rapida per il distrbution Linux che scelto: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Configurare per le connessioni remote: 
    * Passare al [regole del Firewall](https://console.cloud.google.com/networking/firewalls)
    * Aggiungere una regola in entrata per consentire il traffico sulla porta in cui SQL Server è in ascolto (impostazione predefinita TCP: 1433)
