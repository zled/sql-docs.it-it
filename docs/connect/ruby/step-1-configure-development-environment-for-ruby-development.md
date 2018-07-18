---
title: "Passaggio 1: Configurare l'ambiente di sviluppo per lo sviluppo Ruby | Documenti Microsoft"
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: ruby
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8cdbadeb-f640-406c-977c-d2d44b7b5368
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c8b4cd36a78952e8d783e79388ede49287e5e0f7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>Passaggio 1: Configurare l'ambiente di sviluppo per lo sviluppo Ruby
È necessario configurare l'ambiente di sviluppo con i prerequisiti per sviluppare un'applicazione utilizzando il Driver Ruby per SQL Server.    
  
Si noti che il Driver Ruby utilizza il protocollo TDS, che è abilitato per impostazione predefinita in SQL Server e Database SQL di Azure.  Non è richiesta alcuna configurazione aggiuntiva.  
  
  
## <a name="windows"></a>Windows  
  
1.  **Scaricare Ruby programma di installazione**  
Se il computer non ha Ruby installarlo. Per i nuovi utenti ruby, è consigliabile che utilizzare programmi di installazione 2.2 Ruby. Che forniscono una lingua stabile e un elenco completo dei pacchetti (risorse) che sono compatibili e aggiornati. Passare il [pagina di download Ruby](http://rubyinstaller.org/downloads/) e scaricare il programma di installazione appropriato 2.1. x. Per esempio, se si utilizza un computer a 64 bit, scaricare il programma di installazione Ruby 2.1.6 (x64).   
  
2.  **Installare Ruby**  
Una volta scaricato il programma di installazione, eseguire le operazioni seguenti:  
A. Fare doppio clic sul file per avviare il programma di installazione.  
B. Selezionare la lingua e accettare le condizioni.  
c.  Nella schermata delle impostazioni di installazione, selezionare le caselle di controllo accanto a entrambi gli eseguibili aggiungere Ruby a percorso e associare RB .rbw file e con questa installazione Ruby.  
  
3.  **Scaricare Ruby Kit di sviluppo**  
Scaricare Kit dalla pagina RubyInstaller  
  
4.  **Installare Ruby Kit di sviluppo**  
Al termine dell'operazione di download, eseguire le operazioni seguenti:  
A. Fare doppio clic sul file. Verrà richiesto la posizione in cui estrarre i file.  
B. Fare clic sul pulsante "…" e selezionare "C:\DevKit". Probabilmente è necessario creare innanzitutto la cartella, fare clic su "Crea nuova cartella".  
c. Fare clic su "OK" e "Estrarre", per estrarre i file.  
  
5. **Aprire cmd.exe**  
  
6. **Inizializzare Ruby Kit di sviluppo**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **Installare TinyTDS indicatore**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Apri terminal**  
  
2. **Installa Gestione versione Ruby (rvm) e i prerequisiti**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Consente di installare Ruby rvm**  
Ad esempio, installare la versione 2.3.0 di Ruby:  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Assicurarsi che l'output dell'ultimo comando si esegue la versione 2.3.0.  
  
4.  **Installazione di disporre di FreeTDS**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **Installare TinyTDS**  
```  
> gem install tiny_tds  
```  
  
## <a name="mac"></a>Mac  
  
Si noti che Mac OS X già ha Ruby pre-installato, il sistema operativo con una dipendenza.    
  
1.  **Apri terminal**  
  
2. **Installare Gestione pacchetti di Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **Installazione di disporre di FreeTDS**  
```  
> brew install FreeTDS  
```  
  
4.  **Installare TinyTDS indicatore**  
```  
> gem install tiny_tds  
```
