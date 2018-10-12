---
title: "Passaggio 1: Configurare l'ambiente di sviluppo per lo sviluppo Node.js | Microsoft Docs"
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 823177f8fef91dda8cf879f6be84ef6706224fad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600239"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Passaggio 1: Configurare l'ambiente di sviluppo per lo sviluppo Node.js
È necessario configurare l'ambiente di sviluppo con i prerequisiti per lo sviluppo di un'applicazione usando il Driver Node. js per SQL Server.  Il metodo più comune consiste nell'usare node package manager (npm) per installare il modulo noioso, ma è possibile scaricare il modulo tedious direttamente al [Github](https://github.com/pekim/tedious) se si preferisce.  
  
Si noti che il Driver Node. js Usa il protocollo TDS, che è abilitato per impostazione predefinita in SQL Server e Database SQL di Azure.  Non è richiesta alcuna configurazione aggiuntiva.  
  
## <a name="windows"></a>Windows  
  
1. **Installare Gestione pacchetti npm e runtime di Node. js**  
A. Passare a [Node. js](https://nodejs.org/en/download/)  
B. Fare clic sul collegamento appropriato Windows installer msi.   
c. Al termine del download, eseguire il file msi per installare Node. js  
  
2. **Aprire cmd.exe**  
  
3. **Creare una directory del progetto** e spostarsi su di esso.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Creare un progetto Node.**  Per mantenere i valori predefiniti durante la creazione del progetto, premere INVIO fino a quando non viene creato il progetto. Alla fine di questo passaggio, si dovrebbe vedere un file package. JSON nella directory del progetto.  
```  
> npm init  
```  
  
5. **Installare il modulo di noioso nel progetto.**  Si tratta dell'implementazione del protocollo TDS che il driver utilizza per comunicare con SQL Server.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Apri terminale**  
  
2. **Installare il runtime di Node. js**  
```  
>sudo apt-get install node  
```  
3. **Installare npm (Gestione pacchetti di nodi)**  
```  
> sudo apt-get install npm  
```  
4. **Creare una directory del progetto** e spostarsi su di esso.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Creare un progetto Node.**  Per mantenere i valori predefiniti durante la creazione del progetto, premere INVIO fino a quando non viene creato il progetto. Alla fine di questo passaggio, si dovrebbe vedere un file package. JSON nella directory del progetto.  
```  
> sudo npm init  
```  
  
6. **Installare il modulo di noioso nel progetto.**  Si tratta dell'implementazione del protocollo TDS che il driver utilizza per comunicare con SQL Server.  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installare Gestione pacchetti npm e runtime di Node. js**  
A. Passare a [Node. js](https://nodejs.org/en/download/)  
B. Fare clic sul collegamento appropriato programma di installazione Mac OS.  
c. Al termine del download, eseguire il gateway di gestione dati per installare Node. js  
  
2. **Apri terminale**  
  
3. **Creare una directory del progetto** e spostarsi su di esso.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Creare un progetto Node.**  Per mantenere i valori predefiniti durante la creazione del progetto, premere INVIO fino a quando non viene creato il progetto. Alla fine di questo passaggio, si dovrebbe vedere un file package. JSON nella directory del progetto.  
```  
> npm init  
```  
  
5. **Installare il modulo di noioso nel progetto.**  Si tratta dell'implementazione del protocollo TDS che il driver utilizza per comunicare con SQL Server.  
```  
> npm install tedious  
```  
  
