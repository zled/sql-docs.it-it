---
title: "Passaggio 1: Configurare l'ambiente di sviluppo per lo sviluppo di Node.js | Documenti Microsoft"
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: node-js
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 313adb458786f009cd2cbd4fa86c09d7d5302b29
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Passaggio 1: Configurare l'ambiente di sviluppo per lo sviluppo di Node.js
È necessario configurare l'ambiente di sviluppo con i prerequisiti per sviluppare un'applicazione utilizzando il Driver di Node.js per SQL Server.  Il metodo più comune consiste nell'utilizzare la gestione di pacchetti di nodo (npm) per installare il modulo noioso, ma è possibile scaricare il modulo noioso direttamente [Github](https://github.com/pekim/tedious) se si preferisce.  
  
Si noti che il Node.js Driver utilizza il protocollo TDS, che è abilitato per impostazione predefinita in SQL Server e Database SQL di Azure.  Non è richiesta alcuna configurazione aggiuntiva.  
  
## <a name="windows"></a>Windows  
  
1. **Installare Gestione pacchetti npm e runtime Node. js**  
A. Passare a [Node. js](https://nodejs.org/en/download/)  
B. Fare clic sul collegamento appropriato Windows installer msi.   
c. Una volta scaricata, eseguire il file msi per installare Node.js  
  
2. **Aprire cmd.exe**  
  
3. **Creare una directory del progetto** e passare a esso.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Creare un progetto di nodo.**  Per mantenere le impostazioni predefinite durante la creazione del progetto, premere INVIO fino a quando non viene creato il progetto. Alla fine di questo passaggio, verrà visualizzato un file package. JSON nella directory del progetto.  
```  
> npm init  
```  
  
5. **Installa modulo noioso nel progetto.**  Si tratta dell'implementazione del protocollo TDS che utilizza il driver per comunicare con SQL Server.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Apri terminal**  
  
2. **Installare il runtime di Node. js**  
```  
>sudo apt-get install node  
```  
3. **Installare npm (gestione di pacchetti di nodi)**  
```  
> sudo apt-get install npm  
```  
4. **Creare una directory del progetto** e passare a esso.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Creare un progetto di nodo.**  Per mantenere le impostazioni predefinite durante la creazione del progetto, premere INVIO fino a quando non viene creato il progetto. Alla fine di questo passaggio, verrà visualizzato un file package. JSON nella directory del progetto.  
```  
> sudo npm init  
```  
  
6. **Installa modulo noioso nel progetto.**  Si tratta dell'implementazione del protocollo TDS che utilizza il driver per comunicare con SQL Server.  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installare Gestione pacchetti npm e runtime Node. js**  
A. Passare a [Node. js](https://nodejs.org/en/download/)  
B. Fare clic sul collegamento di programma di installazione di Mac OS appropriato.  
c. Una volta scaricati, eseguire il dmg per installare Node.js  
  
2. **Apri terminal**  
  
3. **Creare una directory del progetto** e passare a esso.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Creare un progetto di nodo.**  Per mantenere le impostazioni predefinite durante la creazione del progetto, premere INVIO fino a quando non viene creato il progetto. Alla fine di questo passaggio, verrà visualizzato un file package. JSON nella directory del progetto.  
```  
> npm init  
```  
  
5. **Installa modulo noioso nel progetto.**  Si tratta dell'implementazione del protocollo TDS che utilizza il driver per comunicare con SQL Server.  
```  
> npm install tedious  
```  
  
