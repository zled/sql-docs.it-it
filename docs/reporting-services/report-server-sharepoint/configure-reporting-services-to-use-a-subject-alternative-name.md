---
title: Configurare Reporting Services per utilizzare un nome alternativo del soggetto | Documenti Microsoft
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 73f48b2978055481f1ee93952fb3a35eb84ec416
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a>Configurare Reporting Services per utilizzare un nome alternativo del soggetto

In questo argomento viene illustrato come configurare Reporting Services (SSRS) per utilizzare un nome alternativo del soggetto (SAN) modificando il file RSReportServer. config e usando lo strumento Netsh.exe.

Le istruzioni si applicano all'URL Reporting Service nonché all'URL servizio Web.

Per usare un nome alternativo del soggetto, è necessario che il certificato SSL sia registrato nel server, firmato e che contenga la chiave privata. Non è possibile usare un certificato autofirmato.  
  
 Gli URL in Reporting Services possono essere configurati per utilizzare un certificato SSL. In genere, un certificato contiene solo un nome del soggetto che consente un solo URL per una sessione SSL (Secure Sockets Layer). La SAN è un campo aggiuntivo nel certificato che consente a un servizio SSL per l'ascolto per molti URL e di condividere la porta SSL con altre applicazioni. La SAN è simile `www.s2.com`.  
  
 Per ulteriori informazioni sulle impostazioni SSL per Reporting Services, vedere [configurare connessioni SSL in un Server di Report in modalità nativa](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).  
  
## <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a>Configurare SSRS per usare un nome alternativo del soggetto per l'URL del servizio web
  
1.  Avviare Gestione configurazione Reporting Services.  
  
     Per altre informazioni, vedere [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).  
  
2.  Nella pagina **URL servizio Web** selezionare una porta SSL e un certificato SSL.  
  
     ![Gestione configurazione Reporting Services](../../reporting-services/report-server-sharepoint/media/reportingservices-configurationmanager.png "Gestione configurazione Reporting Services")  
  
     Gestione configurazione registra il certificato SSL per la porta.  
  
3.  Aprire il file rsreportserver.config.  
  
     Per la modalità nativa di SSRS, il file si trova per impostazione predefinita nella cartella seguente:  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
4.  Copiare la sezione URL del servizio Web ReportServer.  
  
     Ad esempio, è la seguente sezione URL originale:  
  
    ```  
        <URL>  
         <UrlString>https://localhost:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
     La seguente sezione URL modificata è:
  
    ```  
    <URL>  
         <UrlString>https://www.s1.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
        <URL>  
         <UrlString>https://www.s2.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
5.  Salvare il file rsreportserver.config.  
  
6.  Avviare un prompt dei comandi come amministratore ed eseguire lo strumento Netsh.exe.  
  
    ```  
    C:\windows\system32\netsh  
    ```  
  
7.  Passare al contesto http digitando il testo seguente.  
  
    ```  
    Netsh>http  
    ```  
  
8.  Mostrare gli urlacl esistenti digitando quanto segue:
  
    ```  
    Netsh http>show urlacl  
    ```  
  
     Verrà visualizzata una voce simile alla seguente.  
  
    ```  
    Reserved URL            : https:// www.s1.com:443/ReportServer/  
        User: NT SERVICE\ReportServer  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)  
    ```  
  
     Un urlacl è un elenco di controllo di accesso discrezionale (DACL, Discretionary Access Control List) per un URL riservato.  
  
9. Creare una nuova voce per il nome alternativo del soggetto con lo stesso utente e SDDL della voce esistente digitando il testo seguente.  
  
    ```  
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer    
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)  
  
    ```  
  
10. Nella pagina **Stato server di report** di Gestione configurazione Reporting Services fare clic su **Arresta** e quindi su **Avvia** per riavviare il server di report.  
  
## <a name="see-also"></a>Vedere anche

 [File di configurazione Rsreportserver. config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Gestione configurazione Reporting Services](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Modificare un file di configurazione di Reporting Services](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [Configurare gli URL di Server di Report](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
