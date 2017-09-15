---
title: Problemi di progettazione di sicurezza ADO | Documenti Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: sql-non-specified
ms.technology: "“drivers”"
ms.topic: article
helpviewer_keywords:
- ADO, security
ms.assetid: 86b83a38-efdf-4831-a6d5-7e470d517d1c
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 51c7e3cf9c99bdd76ce1b84a7c387b1e6e4d2f58
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="ado-security-design-features"></a>Funzionalità di progettazione sicurezza ADO
Le sezioni seguenti descrivono le funzionalità di progettazione della protezione in oggetti ADO (ActiveX Data) 2.8 e versioni successive. Queste modifiche sono state apportate in ADO 2.8 per migliorare la sicurezza. ADO 6.0, incluso in Windows DAC 6.0 in Windows Vista, è funzionalmente equivalente al ADO 2.8, è stato incluso in MDAC 2.8 in Windows XP e Windows Server 2003. In questo argomento vengono fornite informazioni su come proteggere meglio le applicazioni ADO 2.8 o versioni successive.

> [!IMPORTANT]
>  Se si aggiorna l'applicazione da una versione precedente di ADO, è consigliabile testare l'applicazione aggiornata in un computer non di produzione prima di distribuirlo ai clienti. In questo modo, è possibile garantire che essere a conoscenza di eventuali problemi di compatibilità prima di distribuire l'applicazione aggiornata.

## <a name="internet-explorer-file-access-scenarios"></a>Scenari di accesso ai File di Internet Explorer
 L'effetto di funzionalità seguente funzionamento ADO 2.8 e versioni successiva quando è utilizzata in basato su script per le pagine Web in Internet Explorer.

### <a name="revised-and-improved-security-warning-message-box-now-used-to-alert-users"></a>Finestra di messaggio di avviso rivisti e una migliore sicurezza ora utilizzato per avvertire gli utenti
 Per ADO 2.7 e versioni precedente, il seguente messaggio di avviso viene visualizzato quando una pagina Web tramite script tenta di eseguire codice ADO da un provider non attendibile:

```
This page accesses data on another domain. Do you want to allow this? To
avoid this message in Internet Explorer, you can add a secure Web site to
your Trusted Sites zone on the Security tab of the Internet Options dialog
box.
```

 Per ADO 2.8 e versioni successiva, il messaggio precedente non è più visualizzato. Al contrario, il messaggio seguente viene visualizzato in questo contesto:

```
This Website uses a data provider that may be unsafe. If you trust the
Website, click OK, otherwise click Cancel.
```

 Il precedente messaggio consente all'utente di prendere decisioni informate, sapendo le conseguenze per entrambe le possibilità:

-   Se l'utente considera attendibile il sito, fare clic su OK consente tutto il codice indipendente dai disco (tutti i metodi e proprietà ADO con le eccezioni delle API accessibile con disco descritte più avanti in questo argomento) per eseguire e nella finestra del browser.

-   Se l'utente non considera attendibile il sito, fare clic su Annulla blocca il codice di ADO per accedere ai dati di esecuzione ed eseguire nella sua interezza.

### <a name="disk-accessible-code-limited-now-to-trusted-sites"></a>Codice accessibile con disco limitato a questo punto per siti attendibili
 Sono state apportate modifiche di Progettazione aggiuntive in ADO 2.8, in particolare limitare la possibilità di un set limitato di API, che potrebbero esporre la possibilità di leggere o scrivere file nel computer locale. Ecco i metodi dell'API che sono stati ulteriormente limitate per motivi di sicurezza durante l'esecuzione di Internet Explorer:

-   Per l'oggetto ADO **flusso** oggetto, se il [LoadFromFile](../../ado/reference/ado-api/loadfromfile-method-ado.md) o [SaveToFile](../../ado/reference/ado-api/savetofile-method.md) vengono utilizzati metodi.

-   Per ADO **Recordset** dell'oggetto, se il [salvare](../../ado/reference/ado-api/save-method.md) (metodo) o [aprire](../../ado/reference/ado-api/open-method-ado-recordset.md) metodo, ad esempio, quando entrambi il **adCmdFile** opzione è impostata o il [Microsoft OLE DB Provider di persistenza (MSPersist)](../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) viene utilizzato.

 Per questi set limitato di funzioni potenzialmente disco accessibile, verifica quanto segue per ADO 2.8 e versioni successiva, se il codice che utilizza questi metodi viene eseguito in Internet Explorer:

-   Se il sito che ha fornito il codice è stato già aggiunto all'elenco area siti attendibili, il codice viene eseguito nel browser e viene concesso l'accesso ai file locali.

-   Se il sito non viene visualizzato nell'elenco area siti attendibili, il codice viene bloccato e viene negato l'accesso ai file locali.

    > [!NOTE]
    >  In ADO 2.8 e versioni successiva, l'utente non ricevere un avviso o consigliabile aggiungere siti all'elenco area siti attendibili. La gestione dell'elenco siti attendibili è pertanto responsabilità degli utenti che distribuiscono o il supporto di applicazioni basate su siti Web che richiedono l'accesso al file system locale.

### <a name="access-blocked-to-the-activecommand-property-on-recordset-objects"></a>Accesso bloccato per la proprietà ActiveCommand degli oggetti di Recordset
 Quando si esegue Internet Explorer, ADO 2.8 ora blocca l'accesso per il [ActiveCommand](../../ado/reference/ado-api/activecommand-property-ado.md) proprietà per un oggetto attivo **Recordset** specificato e restituisce un errore. L'errore si verifica indipendentemente dal fatto che la pagina deriva da un sito Web registrata nell'elenco siti attendibili.

### <a name="changes-in-handling-for-ole-db-providers-and-integrated-security"></a>Modifiche nella gestione per i provider OLE DB e la sicurezza integrata
 Durante la revisione ADO 2.7 e nelle versioni precedenti per potenziali problemi di sicurezza e problemi, è stato individuato lo scenario seguente:

 In alcuni casi, i provider OLE DB che supportano la sicurezza integrata [DBPROP_AUTH_INTEGRATED](https://msdn.microsoft.com/library/windows/desktop/ms712973.aspx) proprietà potenzialmente potrebbe consentire l'utilizzo tramite script pagine Web di riutilizzare l'oggetto ADO Connection involontariamente connettersi ad altri server utilizzando le credenziali di accesso corrente degli utenti. Per evitare questo problema, ADO 2.8 e versioni successiva di gestire i provider OLE DB a seconda di come si è scelto di fornire oppure non viene fornito, per la sicurezza integrata.

 Per le pagine Web che vengono caricate dai siti elencati nell'elenco area siti attendibili, nella tabella seguente fornisce un riepilogo delle modalità di gestione delle connessioni ADO in ogni caso ADO 2.8 e versioni successiva.

|Le impostazioni di Internet Explorer per l'autenticazione utente, accesso|Provider sono supportati "Integrated Security" e UID e PWD specificato (SQLOLEDB)|Il provider non supporta "Integrated Security" (JOLT, MSDASQL, MSPersist)|Il provider supporta "Integrated Security" ed è impostato su SSPI (nessun UID/PWD vengono specificati)|
|------------------------------------------------|----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
|Accesso automatico con nome utente corrente e la password|Consenti connessione|Consenti connessione|Consenti connessione|
|Richiedi nome utente e password|Consenti connessione|Connessione ha esito negativo|Connessione ha esito negativo|
|Accesso automatico solo nell'area Intranet|Consenti connessione|Chiedi conferma all'utente un avviso di protezione|Chiedi conferma all'utente un avviso di protezione|
|Accesso anonimo|Consenti connessione|Connessione ha esito negativo|Connessione ha esito negativo|

 Nel caso in cui viene visualizzato un avviso di protezione a questo punto, la finestra di messaggio informa l'utente:

```
This Website is using your identity to access a data source. If you trust this Website, click OK, otherwise click Cancel.
```

 Il precedente messaggio consente all'utente di prendere una decisione più oculata e procedere di conseguenza.

> [!NOTE]
>  Per i siti non attendibili (i siti non è elencati nell'elenco area siti attendibili), se il provider è anche non attendibile (come indicato in precedenza in questa sezione), l'utente potrebbe essere consultate due avvisi di sicurezza in una riga, un avviso sul provider di tipo unsafe e secondo la tentativo di utilizzare la propria identità. Se l'utente fa clic su OK per il primo avviso, vengono eseguite le impostazioni di Internet Explorer e un codice di risposta del comportamento descritto nella tabella precedente.

## <a name="controlling-whether-password-text-is-returned-in-ado-connection-strings"></a>Controllare se il testo della password verrà restituito nelle stringhe di connessione ADO
 Quando si tenta di ottenere il valore della [ConnectionString](../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà in un oggetto ADO **connessione** dell'oggetto, si verificano gli eventi seguenti:

1.  Se la connessione è aperta, una chiamata di inizializzazione viene quindi eseguita per il provider OLE DB sottostante per ottenere la stringa di connessione.

2.  A seconda dell'impostazione nel provider OLE DB del [DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO](https://msdn.microsoft.com/library/windows/desktop/ms714905.aspx) proprietà, le password sono incluse insieme alle altre informazioni sulla stringa di connessione che viene restituiti.

 Ad esempio, se la proprietà di connessione ADO dinamica **Persist Security Info** è impostato su **True**, informazioni sulla password è incluso nella stringa di connessione restituita. In caso contrario, se il provider sottostante ha impostato la proprietà su **False** (ad esempio con il provider SQLOLEDB), informazioni relative alle password viene omesso nella stringa di connessione restituito.

 Se si utilizza di terze parti (vale a dire non Microsoft) provider OLE DB con il codice dell'applicazione ADO, è possibile controllare il modo in **DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO** proprietà viene implementata per determinare se inclusione di informazioni sulla password con le stringhe di connessione ADO è consentiti.

## <a name="checking-for-non-file-devices-when-loading-and-saving-recordsets-or-streams"></a>Verifica per i dispositivi non basati su file durante il caricamento e salvataggio di recordset o flussi
 Per ADO 2.7 e versioni precedente, file di input/output operazioni, ad esempio [aprire](../../ado/reference/ado-api/open-method-ado-recordset.md) e [salvare](../../ado/reference/ado-api/save-method.md) che sono stati usati per leggere e scrivere dati su file potrebbe consentire in alcuni casi un nome file o URL da utilizzare che specificato un diverso da un disco in base a tipo di file. Ad esempio, LPT1, COM2, PRN. TXT, AUX possono essere utilizzate come alias per l'input/output tra le stampanti e dispositivi ausiliari nel sistema usando determinati

 Per ADO 2.8 e versioni successiva, questa funzionalità è stata aggiornata. Per aprire e salvare **Recordset** e **flusso** gli oggetti ADO esegue ora un controllo del tipo di file per assicurarsi che il dispositivo di input o output specificato in un URL o un nome file sia un file effettivo.

> [!NOTE]
>  Controllo dei tipi di file come descritto in questa sezione si applica solo per Windows 2000 e versioni successive. Non è applicabile alle situazioni in cui ADO 2.8 o versioni successive è in esecuzione in versioni precedenti di Windows, ad esempio Windows 98.

