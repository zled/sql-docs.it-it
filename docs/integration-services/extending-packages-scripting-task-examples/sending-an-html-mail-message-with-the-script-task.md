---
title: "Invio di un messaggio di posta elettronica HTML con l'attività Script | Documenti Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Send Mail task [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], HTML mail message
ms.assetid: dd2b1eef-b04f-4946-87ab-7bc56bb525ce
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: b5f50a79ca83243ea130c77a0d95ab402ba2d31a
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="sending-an-html-mail-message-with-the-script-task"></a>Invio di un messaggio di posta HTML con l'attività Script
  L'attività SendMail di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] supporta solo messaggi di posta in formato di testo normale. Tuttavia è possibile inviare facilmente messaggi di posta HTML tramite l'attività Script e le funzionalità di posta di .NET Framework.  
  
> [!NOTE]  
>  Se si desidera creare un'attività da riutilizzare più facilmente con più pacchetti, è possibile utilizzare il codice di questo esempio di attività Script come punto iniziale per un'attività personalizzata. Per altre informazioni, vedere [Sviluppo di un'attività personalizzata](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 L'esempio seguente usa il **System.Net.Mail** dello spazio dei nomi per configurare e inviare un messaggio di posta elettronica HTML. Lo script ottiene i campi a, da, oggetto e il corpo del messaggio di posta elettronica dalle variabili del pacchetto, li utilizza per creare un nuovo **MailMessag**e ne imposta il relativo **IsBodyHtml** proprietà **True**. Quindi Ottiene il nome del server SMTP da un'altra variabile del pacchetto, Inizializza un'istanza di **SmtpClient**e chiama il relativo **inviare** metodo per inviare il messaggio HTML. Nell'esempio il messaggio viene incapsulato inviando la funzionalità in una subroutine che potrebbe essere riutilizzata in altri script.  
  
#### <a name="to-configure-this-script-task-example-without-an-smtp-connection-manager"></a>Per configurare questa attività Script di esempio senza una gestione connessione SMTP  
  
1.  Creare le variabili di stringa denominate `HtmlEmailTo`, `HtmlEmailFrom` e `HtmlEmailSubject` e assegnare i valori appropriati per un messaggio di prova valido.  
  
2.  Creare una variabile di stringa denominata `HtmlEmailBody` e assegnarle una stringa di markup HTML. Esempio:  
  
    ```  
    <html><body><h1>Testing</h1><p>This is a <b>test</b> message.</p></body></html>  
    ```  
  
3.  Creare una variabile di stringa denominata `HtmlEmailServer` e assegnare il nome di un server SMTP disponibile che accetta messaggi in uscita anonimi.  
  
4.  Tutte queste cinque variabili per assegnare il **ReadOnlyVariables** proprietà di una nuova attività Script.  
  
5.  Importazione di **System.Net** e **System.Net.Mail** gli spazi dei nomi nel codice.  
  
 Il codice di esempio in questo argomento ottiene il nome del server SMTP da una variabile del pacchetto. Tuttavia, è possibile sfruttare anche una gestione connessione SMTP per incapsulare le informazioni di connessione ed estrarre il nome del server dalla gestione connessione nel codice. Il metodo <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> della gestione connessione SMTP restituisce una stringa nel formato seguente:  
  
 `SmtpServer=smtphost;UseWindowsAuthentication=False;EnableSsl=False;`  
  
 È possibile utilizzare il **String. Split** (metodo) per separare questo elenco di argomenti in una matrice di stringhe singole in corrispondenza di ogni punto e virgola (;) o uguale (=) di accedere e quindi estrarre il secondo argomento (pedice 1) dalla matrice come nome del server.  
  
#### <a name="to-configure-this-script-task-example-with-an-smtp-connection-manager"></a>Per configurare questa attività Script di esempio con una gestione connessione SMTP  
  
1.  Modificare l'attività Script configurata precedentemente rimuovendo la `HtmlEmailServer` variabile dall'elenco di **ReadOnlyVariables**.  
  
2.  Sostituire la riga di codice che ottiene il nome del server:  
  
    ```  
    Dim smtpServer As String = _  
      Dts.Variables("HtmlEmailServer").Value.ToString  
    ```  
  
     con le righe seguenti:  
  
    ```  
    Dim smtpConnectionString As String = _  
      DirectCast(Dts.Connections("SMTP Connection Manager").AcquireConnection(Dts.Transaction), String)  
    Dim smtpServer As String = _  
      smtpConnectionString.Split(New Char() {"="c, ";"c})(1)  
    ```  
  
## <a name="code"></a>Codice  
  
```vb  
Public Sub Main()  
  
  Dim htmlMessageTo As String = _  
    Dts.Variables("HtmlEmailTo").Value.ToString  
  Dim htmlMessageFrom As String = _  
    Dts.Variables("HtmlEmailFrom").Value.ToString  
  Dim htmlMessageSubject As String = _  
    Dts.Variables("HtmlEmailSubject").Value.ToString  
  Dim htmlMessageBody As String = _  
    Dts.Variables("HtmlEmailBody").Value.ToString  
  Dim smtpServer As String = _  
    Dts.Variables("HtmlEmailServer").Value.ToString  
  
  SendMailMessage( _  
      htmlMessageTo, htmlMessageFrom, _  
      htmlMessageSubject, htmlMessageBody, _  
      True, smtpServer)  
  
  Dts.TaskResult = ScriptResults.Success  
  
End Sub  
  
Private Sub SendMailMessage( _  
    ByVal SendTo As String, ByVal From As String, _  
    ByVal Subject As String, ByVal Body As String, _  
    ByVal IsBodyHtml As Boolean, ByVal Server As String)  
  
  Dim htmlMessage As MailMessage  
  Dim mySmtpClient As SmtpClient  
  
  htmlMessage = New MailMessage( _  
    SendTo, From, Subject, Body)  
  htmlMessage.IsBodyHtml = IsBodyHtml  
  
  mySmtpClient = New SmtpClient(Server)  
  mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials  
  mySmtpClient.Send(htmlMessage)  
  
End Sub  
```  
  
```csharp  
public void Main()  
        {  
  
            string htmlMessageTo = Dts.Variables["HtmlEmailTo"].Value.ToString();  
            string htmlMessageFrom = Dts.Variables["HtmlEmailFrom"].Value.ToString();  
            string htmlMessageSubject = Dts.Variables["HtmlEmailSubject"].Value.ToString();  
            string htmlMessageBody = Dts.Variables["HtmlEmailBody"].Value.ToString();  
            string smtpServer = Dts.Variables["HtmlEmailServer"].Value.ToString();  
  
            SendMailMessage(htmlMessageTo, htmlMessageFrom, htmlMessageSubject, htmlMessageBody, true, smtpServer);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
        private void SendMailMessage(string SendTo, string From, string Subject, string Body, bool IsBodyHtml, string Server)  
        {  
  
            MailMessage htmlMessage;  
            SmtpClient mySmtpClient;  
  
            htmlMessage = new MailMessage(SendTo, From, Subject, Body);  
            htmlMessage.IsBodyHtml = IsBodyHtml;  
  
            mySmtpClient = new SmtpClient(Server);  
            mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials;  
            mySmtpClient.Send(htmlMessage);  
  
        }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività Invia messaggi](../../integration-services/control-flow/send-mail-task.md)  
  
  

