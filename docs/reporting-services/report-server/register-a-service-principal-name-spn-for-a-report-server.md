---
title: "Registrare un nome dell'entità servizio (SPN) per un Server di Report | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda91d4f-77cc-4898-ad03-810ece5f8e74
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9518d1bd3ee166a0f21292ca08130214afc841be
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="register-a-service-principal-name-spn-for-a-report-server"></a>Registrare un nome dell'entità servizio (SPN) per un server di report
  Se si distribuisce [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in una rete che utilizza il protocollo Kerberos per l'autenticazione reciproca, è necessario creare un nome dell'entità servizio (SPN) per il server di report se questo è configurato per l'esecuzione come account utente di dominio.  
  
## <a name="about-spns"></a>Informazioni sugli SPN  
 Un SPN è un identificatore univoco per un servizio in una rete che utilizza l'autenticazione Kerberos. Un SPN è costituito da una classe del servizio, un nome host e una porta. In una rete che utilizza l'autenticazione Kerberos un SPN per il server deve essere registrato con un account computer predefinito, ad esempio NetworkService o LocalSystem, o un account utente. Gli SPN vengono registrati automaticamente per gli account predefiniti. Quando, tuttavia, si esegue un servizio utilizzando un account utente di dominio, è necessario registrare manualmente l'SPN per l'account che si desidera utilizzare.  
  
 Per creare un SPN, è possibile usare l'utilità della riga di comando **SetSPN** . Per altre informazioni, vedere quanto segue:  
  
-   [Setspn](http://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (http://technet.microsoft.com/library/cc731241(WS.10).aspx).  
  
-   [Sintassi SetSPN (Setspn.exe) dei nomi dell'entità servizio (SPN)](http://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (http://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx).  
  
 Per eseguire l'utilità nel controller di dominio, è necessario essere un amministratore di dominio.  
  
## <a name="syntax"></a>Sintassi  
 La sintassi del comando per l'utilizzo dell'utilità SetSPN per la creazione di un SPN per il server di report è analoga alla seguente:  
  
```  
Setspn -s http/<computername>.<domainname>:<port> <domain-user-account>  
```  
  
 **SetSPN** è disponibile in Windows Server. L'argomento **-s** aggiunge un nome SPN dopo avere verificato che non sono presenti duplicati. **NOTA:** -s è disponibile in Windows Server a partire da Windows Server 2008.  
  
 **HTTP** è la classe del servizio. Il servizio Web ReportServer viene eseguito in HTTP.SYS. Una conseguenza della creazione di un SPN per HTTP è che a tutte le applicazioni Web presenti nello stesso computer ed eseguite in HTTP.SYS, incluse le applicazioni ospitate in IIS, verranno concessi ticket basati sull'account utente di dominio. Se tali servizi vengono eseguiti con un account diverso, le richieste di autenticazione avranno esito negativo. Per evitare questo problema, assicurarsi di configurare tutte le applicazioni HTTP per l'esecuzione con lo stesso account oppure creare intestazioni host per ogni applicazione e quindi SPN distinti per ciascuna intestazione host. Quando si configurano le intestazioni host, è necessario apportare le modifiche DNS indipendentemente dalla configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 I valori specificati per \< *computername*>, \< *domainname*>, e \< *porta*> identificano l'indirizzo di rete univoco del computer che ospita il server di report. Può trattarsi di un nome host locale o di un nome di dominio completo (FQDN). Se solo un dominio e si utilizza la porta 80, è possibile omettere \< *domainname*> e \< *porta*> dalla riga di comando. \<*account utente di dominio*> è l'account utente con cui viene eseguito il servizio Windows ReportServer e per cui deve essere registrato il nome SPN.  
  
## <a name="register-an-spn-for-domain-user-account"></a>Registrare un SPN per l'account utente di dominio  
  
#### <a name="to-register-an-spn-for-a-report-server-service-running-as-a-domain-user"></a>Per registrare un SPN per un servizio del server di report eseguito come utente di dominio  
  
1.  Installare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e configurare il servizio del server di report per l'esecuzione come account utente di dominio. Si noti che gli utenti non saranno in grado di connettersi al server di report fino a quando non vengono completati i passaggi seguenti.  
  
2.  Accedere al controller di dominio come amministratore di dominio.  
  
3.  Aprire la finestra del prompt dei comandi.  
  
4.  Copiare il comando seguente, sostituendo i valori segnaposto con quelli effettivi, validi per la rete in uso:  
  
    ```  
    Setspn -s http/<computer-name>.<domain-name>:<port> <domain-user-account>  
    ```  
  
     Esempio: `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`  
  
5.  Eseguire il comando.  
  
6.  Aprire il file **RsReportServer.config`<AuthenticationTypes>` e individuare la sezione** .  
  
7.  Aggiungere `<RSWindowsNegotiate/>` come prima voce in questa sezione per abilitare NTLM.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare un Account del servizio &#40; Gestione configurazione SSRS &#41;](http://msdn.microsoft.com/library/25000ad5-3f80-4210-8331-d4754dc217e0)   
 [Configurare Account di servizio del Server di Report &#40; Gestione configurazione SSRS &#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Gestire un Server di Report di Reporting Services in modalità nativa](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  
