---
title: "Registrare il repository di disponibilità generale per SQL Server in Linux | Documenti Microsoft"
description: "Modificare repository dal repository anteprima 2017 di SQL Server nel repository General Availability (GA) in Linux (GA è talvolta anche detto RTM)."
author: annashres
ms.author: anshrest
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 28c5668598c5464c893c1bf62c19699282ecf7b3
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="change-repositories-from-the-preview-repository-to-the-ga-repository"></a>Repository di modifica dal repository di anteprima per il repository GA

Quando si aggiorna SQL Server 2017 CTP 2.1, RC1 o RC2 alla versione GA (General Availability) è necessario passare repository. Le sezioni seguenti illustrano la scelta del repository e su come apportare le modifiche prima dell'aggiornamento.

## <a name="repository-choices"></a>Opzioni di repository

È importante notare che esistono due tipi principali di repository per ogni distribuzione:

  > [!IMPORTANT]
  > Qualsiasi versione precedente alla versione CTP 2.1 è necessario aggiornare a almeno 2.1 prima dell'aggiornamento a GA.

- **Gli aggiornamenti cumulativi (CU)**: l'aggiornamento cumulativo (CU) repository contiene i pacchetti per la versione di SQL Server base ed eventuali correzioni o miglioramenti Release. Gli aggiornamenti cumulativi sono specifici di una versione di rilascio, ad esempio SQL Server 2017. Essi vengono rilasciati a un ritmo regolare.

- **GDR**: GDR il repository contiene i pacchetti per la versione di SQL Server base solo gli aggiornamenti critici e aggiornamenti della sicurezza perché tale versione. Questi aggiornamenti vengono inoltre aggiunti alla versione di aggiornamento Cumulativo successiva.

Ogni versione CU e GDR contiene il pacchetto di SQL Server completo e tutti gli aggiornamenti precedenti per il repository. L'aggiornamento da una versione GDR a una versione aggiornamento Cumulativo è supportato modificando il repository configurato per SQL Server. È anche possibile [effettuare il downgrade](sql-server-linux-setup.md#rollback) per qualsiasi versione entro il numero di versione principale (ad esempio: 2017).

> [!NOTE]
> È possibile aggiornare da una versione GDR a CU rilasciare in qualsiasi momento modificando repository. L'aggiornamento da un pacchetto CU versione a una versione GDR non è supportata. 

## <a name="change-to-a-ga-repository"></a>Modificare in un repository GA

Per modificare dal repository di anteprima per un repository di origine (CU o GDR), utilizzare la procedura seguente:

1. Rimuovere il repository di anteprima configurate in precedenza.

   | Piattaforma | Comando di rimozione del repository |
   |-----|-----|
   | RHEL | `sudo rm -rf /etc/yum.repos.d/mssql-server.repo` |
   | SLES | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
   | Ubuntu | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |

1. Per **Ubuntu solo**, importare le chiavi GPG archivio pubblico.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Configurare il nuovo repository.

   | Piattaforma | Archivio | Command |
   |-----|-----|-----|
   | RHEL | CU | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
   | RHEL | GDR | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |
   | SLES | CU  | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
   | SLES | GDR | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |
   | Ubuntu | CU | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)" && sudo apt-get update` |
   | Ubuntu | GDR | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)" && sudo apt-get update` |

1. [Installare](sql-server-linux-setup.md#platforms) o [aggiornare](sql-server-linux-setup.md#upgrade) SQL Server tramite il repository GA.

   > [!IMPORTANT]
   > A questo punto, se si sceglie di eseguire un'installazione completa utilizzando il [esercitazioni delle Guide rapide](#platforms), tenere presente che si è appena configurato del repository di destinazione. Non ripetere il passaggio nelle esercitazioni. Ciò vale soprattutto se si configura il repository GDR, poiché le esercitazioni utilizzano il repository CU.

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni su come installare SQL Server 2017 in Linux, vedere [Guida all'installazione per SQL Server in Linux](sql-server-linux-setup.md).
