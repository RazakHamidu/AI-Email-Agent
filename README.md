# AI-Email-Agent

Questo progetto automatizza l'invio di email utilizzando un AI agent, sfruttando n8n per l'automazione e l'integrazione dei flussi di lavoro. L'AI agent invia email in base alle istruzioni ricevute tramite un'interfaccia di chat, aiutandoti a risparmiare tempo ed energia.

## Sommario
1. [Panoramica](#panoramica)
2. [Prerequisiti](#prerequisiti)
3. [Installazione](#installazione)
4. [Impostazione del Workflow](#impostazione-del-workflow)
5. [Configurazione delle Credenziali](#configurazione-delle-credenziali)
6. [Configurazione di Pinecone](#configurazione-di-pinecone)
7. [Esecuzione dell'AI Agent](#esecuzione-dellai-agent)
8. [Tech Stack](#tech-stack)

## Panoramica
Questo AI Agent automatizza la risposta alle email per conto tuo. Utilizza un modello LLM (GPT-4o-mini) per comporre e inviare email, gestendo la tua casella di posta e liberando tempo.

## Prerequisiti
Prima di iniziare, assicurati di avere i seguenti strumenti:
- **n8n**: Strumento di automazione dei flussi di lavoro, preferibilmente in modalità self-hosted. [Guida all'installazione di n8n](https://n8n.io/).
- **Pinecone**: Un database vettoriale utilizzato per memorizzare e interrogare i contatti email. [Pinecone](https://www.pinecone.io/).
- **Google Docs API & Gmail API**: Utilizzate per accedere alle informazioni di contatto e inviare email. Segui la [guida OAuth di n8n](https://docs.n8n.io/integrations/builtin/credentials/google/oauth-single-service/#google-cloud-app-becoming-unauthorized).
- **API OpenAI**: Utilizza il modello GPT-4o-mini per il natural language processing. [Chiavi API OpenAI](https://platform.openai.com/api-keys).
- Una lista di contatti salvata su Google Docs con il seguente formato: Nome | Cognome | Indirizzo Email


## Installazione
1. **Importa i Flussi di Lavoro**:
  - Accedi a n8n.
  - Crea un nuovo workflow.
  - ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/3b9c45bc-36da-45d7-aa64-5ddceedb5dca/ade46dea-c7ae-4757-a3b9-b7d7183e0ddf/image.png)
  - Importa i seguenti file JSON:
      - `AI_Email_Agent.json`
      - `Push_data_to_Pinecone.json`
      - `Send_email.json`
  - Ogni file deve essere importato in workflow distinti.

2. **Configura le Credenziali**:
  - Ogni nodo nel workflow richiede specifiche credenziali:
      - Pinecone per la gestione dei dati.
      - Google API per accedere ai contatti e inviare email.
      - OpenAI API per la generazione delle email tramite AI.
  - Segui la documentazione specifica di n8n per ciascun servizio.

## Impostazione del Workflow
1. Crea un workflow su n8n importando i tre file JSON indicati sopra.
2. Dopo averli importati, assicurati che tutti i nodi siano configurati correttamente per comunicare tra Pinecone, Google Docs API, Gmail API e OpenAI.

## Configurazione delle Credenziali
- Dovrai fornire le credenziali API per ogni servizio utilizzato nel workflow:
  - **Pinecone**: Necessario per importare e recuperare la lista di contatti.
  - **Google API**: Sia Gmail che Docs API sono richiesti per gestire i contatti e inviare email.
  - **OpenAI API**: Necessaria per utilizzare il modello GPT e generare il contenuto delle email.

## Configurazione di Pinecone
1. Accedi a Pinecone e crea un indice.
2. Usa la seguente configurazione:
 - Seleziona `text-embedding-3-large`.
3. Chiudi la configurazione e conferma l'integrazione con il workflow di n8n.

## Esecuzione dell'AI Agent
Una volta configurati i workflow e le credenziali, puoi eseguire l'AI Agent:
1. Apri il workflow `AI_Email_Agent` su n8n.
2. Clicca su **Start** per avviare il processo.
3. L'AI agent inizierà a comporre e inviare email in base alle istruzioni ricevute.

## Tech Stack
- **n8n**: Automazione del workflow.
- **OpenAI GPT-4o-mini**: LLM.
- **Pinecone**: Database vettoriale per la gestione dei contatti.
- **Google Docs API**: Accesso alla lista di contatti.
- **Google Gmail API**: Per l'invio delle email.

