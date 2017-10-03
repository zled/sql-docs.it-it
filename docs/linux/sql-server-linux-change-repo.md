---
title: "Registrare il repository disponibilità generale per SQL Server in Linux | Documenti Microsoft"
description: "Modificare repository dal repository anteprima 2017 di SQL Server nel repository General Availability (GA) in Linux (GA è talvolta anche detto RTM)."
author: annashres
ms.author: anshrest
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 5522fa5a1ac48f2484c38abd7a545b6b319af71f
ms.contentlocale: it-it
ms.lasthandoff: 10/02/2017

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

1. Configurare il nuovo repository.

   | Piattaforma | Archivio | Command |
   |-----|-----|-----|
   | RHEL | AGGIORNAMENTO CUMULATIVO | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
   | RHEL | GDR | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |
   | SLES | AGGIORNAMENTO CUMULATIVO  | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles12/mssql-server-2017.repo` |
   | SLES | GDR | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles12/mssql-server-2017-gdr.repo` |
   | Ubuntu | AGGIORNAMENTO CUMULATIVO | ' sudo curl https://packages.microsoft.com/keys/microsoft.asc \| Sudo apt-chiave add - & & sudo aggiungere apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)" ' |
   | Ubuntu | GDR | ' sudo curl https://packages.microsoft.com/keys/microsoft.asc \| Sudo apt-chiave add - & & sudo aggiungere apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)" ' |

1. Aggiornamento del sistema.

   | Piattaforma | Comando Update |
   |-----|-----|
   | RHEL | `sudo yum update` |
   | SLES | `sudo zypper --gpg-auto-import-keys refresh` |
   | Ubuntu | `sudo apt-get update` |

1. [Installare](sql-server-linux-setup.md#platforms) o [aggiornare](sql-server-linux-setup.md#upgrade) SQL Server tramite il repository GA.

   > [!IMPORTANT]
   > A questo punto, se si sceglie di eseguire un'installazione completa utilizzando il [esercitazioni delle Guide rapide](#platforms), tenere presente che si è appena configurato del repository di destinazione. Non ripetere il passaggio nelle esercitazioni. Ciò vale soprattutto se si configura il repository GDR, poiché le esercitazioni utilizzano il repository CU.

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni su come installare SQL Server 2017 in Linux, vedere [Guida all'installazione per SQL Server in Linux](sql-server-linux-setup.md).

