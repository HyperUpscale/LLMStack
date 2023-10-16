<p align="center">
  <a href="https://llmstack.ai"><img src="https://llmstack.ai/img/llmstack-logo-light-white-bg.svg" alt="LLMStack" width="500px"></a>
</p>
<p align="center">
    <em>LLMStack is a no-code platform for building generative AI applications, chatbots, agents and connecting them to your data and business processes.</em>
</p>
<p align="center">
    <a href="https://llmstack.ai/docs/getting-started/introduction#quickstart" target="_blank">Quickstart</a> | <a href="https://llmstack.ai/docs/" target="_blank">Documentation</a> | <a href="trypromptly.com" target="_blank">Promptly</a>
</p>

## Overview

Build tailor-made generative AI applications, chatbots and agents that cater to your unique needs by chaining multiple LLMs. Seamlessly integrate your own data and GPT-powered models without any coding experience using LLMStack's no-code builder. Trigger your AI chains from Slack or Discord. Deploy to the cloud or on-premise.

## Getting Started
It won't work on Ubuntu 20.04 as LLMStack requires python 3.9. 
It will also not work on any Windows natively, as a required library 'uvloop' is not supported for Windows.

LLMStack deployment comes with a default admin account whose credentials are `admin` and `promptly`.


INSTALLATION

### Install Option 1 - Ubuntu 22.04 

Install LLMStack using pip:

```sh
pip install llmstack
```

Start LLMStack using the following command:

```sh
llmstack
```

Above commands will install and start LLMStack. It will create `.llmstack` in your home directory and places the database and config files in it when run for the first time. Once LLMStack is up and running, it should automatically open your browser and point it to [localhost:3000](http://localhost:3000).

### Install Option 2 - Windows with WSL with Ubuntu 22.04 

cmd
...
wsl --install Ubuntu-22.04
...
sudo apt update
...
sudo apt-get install python3 python3-pip
...
sudo pip install llmstack
...
sudo playwright install-deps
...
llmstack


### Option 3 - If you are on Windows - with DOCKER

This method uses docker compose to bring up the application containers. Clone this repository or download the latest release. Install [docker](https://docs.docker.com/engine/install/) if not already installed. Copy `.env.prod` to `.env` and update `SECRET_KEY`, `CIPHER_SALT` and `DATABASE_PASSWORD` in `.env` file:

```
cp .env.prod .env
```

Run LLMStack using the following command:

```
./run-llmstack.sh
```

, you can use `run-llmstack.bat` instead

Once LLMStack is up and ready, it should automatically open your browser and point it to [localhost:3000](http://localhost:3000). You can also alternatively use `docker compose up` to manually start the containers and open [localhost:3000](http://localhost:3000) to login into the platform. Make sure to wait for the API server to be ready before trying to load LLMStack.

> Remember to update `POSTGRES_VOLUME`, `REDIS_VOLUME` and `WEAVIATE_VOLUME` in `.env` file if you want to persist data across container restarts.


## Features

**🔗 Chain multiple models**: LLMStack allows you to chain multiple LLMs together to build complex generative AI applications.

**📊 Use generative AI on your Data**: Import your data into your accounts and use it in AI chains. LLMStack allows importing various types (_CSV, TXT, PDF, DOCX, PPTX etc.,_) of data from a variety of sources (_gdrive, notion, websites, direct uploads etc.,_). Platform will take care of preprocessing and vectorization of your data and store it in the vector database that is provided out of the box.

**🛠️ No-code builder**: LLMStack comes with a no-code builder that allows you to build AI chains without any coding experience. You can chain multiple LLMs together and connect them to your data and business processes.

**☁️ Deploy to the cloud or on-premise**: LLMStack can be deployed to the cloud or on-premise. You can deploy it to your own infrastructure or use our cloud offering at [Promptly](https://trypromptly.com).

**🚀 API access**: Apps or chatbots built with LLMStack can be accessed via HTTP API. You can also trigger your AI chains from **_Slack_** or **_Discord_**.

**🏢 Multi-tenant**: LLMStack is multi-tenant. You can create multiple organizations and add users to them. Users can only access the data and AI chains that belong to their organization.

## What can you build with LLMStack?

Using LLMStack you can build a variety of generative AI applications, chatbots and agents. Here are some examples:

**📝 Text generation**: You can build apps that generate product descriptions, blog posts, news articles, tweets, emails, chat messages, etc., by using text generation models and optionally connecting your data. Check out this [marketing content generator](https://trypromptly.com/app/50ee8bae-712e-4b95-9254-74d7bcf3f0cb) for example

**🤖 Chatbots**: You can build chatbots trained on your data powered by ChatGPT like [Promptly Help](https://trypromptly.com/app/f4d7cb50-1805-4add-80c5-e30334bce53c) that is embedded on Promptly website

**🎨 Multimedia generation**: Build complex applications that can generate text, images, videos, audio, etc. from a prompt. This [story generator](https://trypromptly.com/app/9d6da897-67cf-4887-94ec-afd4b9362655) is an example

**🗣️ Conversational AI**: Build conversational AI systems that can have a conversation with a user. Check out this [Harry Potter character chatbot](https://trypromptly.com/app/bdeb9850-b32e-44cf-b2a8-e5d54dc5fba4)

**🔍 Search augmentation**: Build search augmentation systems that can augment search results with additional information using APIs. Sharebird uses LLMStack to augment search results with AI generated answer from their content similar to Bing's chatbot

**💬 Discord and Slack bots**: Apps built on LLMStack can be triggered from Slack or Discord. You can easily connect your AI chains to Slack or Discord from LLMStack's no-code app editor. Check out our [Discord server](https://discord.gg/3JsEzSXspJ) to interact with one such bot.

## Administration

Login to [http://localhost:3000/admin](http://localhost:3000/admin) using: "admin", with "promptly"

## Cloud Offering

Check out our cloud offering at [Promptly](https://trypromptly.com). You can sign up for a free account and start building your own generative AI applications.

## Documentation

Check out our documentation at [llmstack.ai/docs](https://llmstack.ai/docs/) to learn more about LLMStack.

## Development

Run the following commands from the root of the repository to bring up the application containers in development mode. Make sure you have [docker](https://docs.docker.com/engine/install/) and [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) installed on your system before running these commands.

```bash
cd client
npm install
npm run build
cd ..
docker compose -f docker-compose.dev.yml --env-file .env.dev up --build
```

This will mount the source code into the containers and restart the containers on code changes. Update `.env.dev` as needed. Please note that LLMStack is available at [http://localhost:9000](http://localhost:9000) in development mode.

> You can skip running `npm install` and `npm run build` if you have already built the client before

For frontend development, you can use `npm start` to start the development server in client directory. You can also use `npm run build` to build the frontend and serve it from the backend server.

To update documentation, make changes to `web/docs` directory and run `npm run build` in web directory to build the documentation. You can use `npm start` in web directory to serve the documentation locally.

## Contributing

They welcome contributions to LLMStack. Please check out their [contributing guide](https://llmstack.ai/docs/guides/contributing) to learn more about how you can contribute to LLMStack.
