---
title: Blocco di riga | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7b41b33aa022bc0a62996e09a713f36bbe04e816
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-row-locking"></a>Informazioni sul blocco di riga
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] blocchi di riga. Questi blocchi consentono di implementare il controllo della concorrenza tra più utenti che eseguono contemporaneamente modifiche in un database. Per impostazione predefinita, le transazioni e i blocchi sono gestiti a livello di singola connessione. Se, ad esempio, tramite un'applicazione vengono aperte due connessioni JDBC, i blocchi acquisiti da una connessione non possono essere condivisi con l'altra connessione. Nessuna delle due connessioni può acquisire blocchi che entrerebbero in conflitto con i blocchi mantenuti attivi dall'altra connessione.  
  
> [!NOTE]  
>  Se viene utilizzato il blocco di riga, tutte le righe nel buffer di recupero sono bloccate, pertanto un'impostazione molto grande per la dimensione di recupero può influire sulla concorrenza.  
  
 Il blocco viene utilizzato per garantire l'integrità delle transazioni e la coerenza dei database. Il blocco impedisce agli utenti di leggere dati di cui è in corso la modifica da parte di altri utenti e impedisce che gli stessi dati vengano modificati contemporaneamente da più utenti. Se il blocco non viene utilizzato, i dati inclusi in un database possono diventare incorretti a livello logico e le query eseguite su tali dati possono produrre risultati imprevisti.  
  
> [!NOTE]  
>  Per ulteriori informazioni sul blocco di riga in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere "utilizzo dei blocchi nel [!INCLUDE[ssDE](../../includes/ssde_md.md)]" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione Online.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei risultati set con il Driver JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  
