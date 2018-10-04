---
title: Accettare le condizioni di licenza | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- license terms
helpviewer_keywords:
- Registration Information page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, Registration Information page
ms.assetid: 08dd739d-5817-4418-bcff-74ab7f8bbd33
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 631ae416116832c725de8335780db87c03811320
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141561"
---
# <a name="accept-license-terms"></a>Accettazione delle condizioni di licenza
  Usare la **accettare le condizioni di licenza** pagina della [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione guidata accettare le condizioni di licenza per questa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 È possibile stampare il contratto di licenza o copiarlo negli Appunti. Per continuare, accettare le condizioni di licenza, quindi scegliere **Avanti**. Per chiudere l'installazione, fare clic su **Annulla**.  
  
## <a name="customer-experience-improvement-program-ceip"></a>Customer Experience Improvement Program (CEIP)  
 Se si abilita la segnalazione CEIP, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene configurato per l'invio periodico di un report a [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Nei report verranno incluse informazioni sulla configurazione hardware in uso e sulle modalità di utilizzo dei componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I dati relativi all'utilizzo delle caratteristiche verranno utilizzati da [!INCLUDE[msCoName](../../includes/msconame-md.md)] per migliorare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tra i componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] monitorati da questa caratteristica sono inclusi quelli indicati di seguito:  
  
-   Il [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Replica  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Programma di installazione  
  
 Informazioni sull'utilizzo delle caratteristiche vengono inviate a [!INCLUDE[msCoName](../../includes/msconame-md.md)], in cui vengono archiviati con accesso limitato.  
  
 Per disabilitare la segnalazione CEIP al termine dell'installazione, usare il  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] segnalazione errori e utilizzo** strumento nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **strumenti di configurazione** menu.  
  
 Per le azioni di installazione quali aggiornamento, ripristino, installazione e così via, le informazioni vengono raccolte e caricate solo durante l'esecuzione del programma di installazione  
  
 Per tutti gli altri componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le informazioni vengono raccolte una volta al giorno per tutte le istanze abilitate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per impostazione predefinita, la raccolta viene eseguita a mezzanotte per ridurre il carico del server. Se si desidera cambiare l'ora di raccolta, è possibile modificare manualmente la chiave del Registro di sistema che la controlla. Ogni istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha la propria chiave del Registro di sistema:  
  
 HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< ID istanza > \CPE\TimeofReporting  
  
 Il valore della chiave del Registro di sistema include l'ora di esecuzione della raccolta espressa in numero di minuti a partire da 00.00 (mezzanotte). Ad esempio, se il valore immesso è 60 la raccolta verrà eseguita alla 1.00, mentre se il valore immesso è 1200 la raccolta verrà eseguita alle 20.00 e così via.  
  
## <a name="error-reporting"></a>Segnalazione errori  
 Usare la **utilizzo Impostazioni segnalazione errori e** pagina della [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione guidata per abilitare la funzionalità errori e utilizzo funzionalità per la creazione di report [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="options"></a>Opzioni  
 Per impostazione predefinita, sono disabilitate per la raccolta dati sull'utilizzo delle caratteristiche e funzionalità di segnalazione errori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i relativi componenti in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Segnalazione errori  
 Se si abilita la funzionalità di segnalazione errori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurato per l'invio di un report per [!INCLUDE[msCoName](../../includes/msconame-md.md)] automaticamente se si verifica un errore irreversibile in uno dei seguenti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] componenti:  
  
-   Il [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Replica  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] utilizza i report degli errori per migliorare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funzionalità e considera tutte le informazioni riservate.  
  
 Le informazioni relative agli errori vengono inviate mediante una connessione protetta (https) a [!INCLUDE[msCoName](../../includes/msconame-md.md)] e archiviate con diritti di accesso limitati. In alternativa, le segnalazioni possono essere inviate al server interno per la segnalazione degli errori (Corporate Error Reporting).  
  
 Nelle segnalazioni degli errori sono incluse le informazioni seguenti:  
  
-   La condizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quando si è verificato il problema.  
  
-   La versione del sistema operativo e le informazioni sull'hardware del computer.  
  
-   L'ID digitale del prodotto che non viene utilizzato per l'identificazione della licenza.  
  
-   L'indirizzo IP di rete del computer o del server proxy.  
  
-   Le informazioni ricavate dalla memoria o dai file del processo che ha generato l'errore.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] non raccoglie intenzionalmente file, nome, indirizzo, indirizzo di posta elettronica o qualsiasi altra forma di informazioni personali. È tuttavia possibile che la segnalazione degli errori contenga informazioni personali ricavate dalla memoria o dai file del processo che ha generato l'errore. Le informazioni raccolte possono contenere dati personali. Tuttavia, tali informazioni non saranno utilizzate da [!INCLUDE[msCoName](../../includes/msconame-md.md)] in alcun modo per identificare l'utente.  
  
 Per altre informazioni sul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] privacy e i criteri di raccolta dati, vedere [informativa sulla Privacy di Microsoft SQL Server](../../../2014/getting-started/microsoft-sql-server-privacy-statement.md).  
  
 Se dopo avere abilitato la funzionalità Segnalazione errori si verifica un errore irreversibile, è possibile che venga visualizzata una risposta da [!INCLUDE[msCoName](../../includes/msconame-md.md)] nel registro eventi di Windows con un collegamento a un articolo della [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base relativo all'errore specifico.  
  
 Per disabilitare la segnalazione di errore o sull'utilizzo delle funzionalità per tutte le istanze del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e relativi componenti al termine dell'installazione, aprire il **utilizzo Impostazioni segnalazione errori e** finestra di dialogo e deselezionare le caselle di controllo per **sull'utilizzo delle funzionalità** . Se **segnalazione errori** è abilitata per più componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]e i componenti condivisi) è possibile disabilitare segnalazione errori per ogni istanza di un singolo componente, nonché i componenti condivisi, elencato come **altri**.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulle condizioni di licenza di SQL Server](../../../2014/getting-started/about-the-sql-server-license-terms.md)  
  
  
