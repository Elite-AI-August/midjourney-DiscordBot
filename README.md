# midjourney-api

Node.js client for the unofficial MidJourney api.  
Major update New [niji bot](https://github.com/erictik/midjourney-api/blob/main/example/imagine-niji.ts) & [custom zoom](https://github.com/erictik/midjourney-api/blob/main/example/customzoom.ts) & [remix mode](https://github.com/erictik/midjourney-api/blob/main/example/variation-ws.ts)
<div align="center">
	<p>
		<a href="https://discord.gg/GavuGHQbV4"><img src="https://img.shields.io/discord/1082500871478329374?color=5865F2&logo=discord&logoColor=white" alt="Discord server" /></a>
		<a href="https://www.npmjs.com/package/midjourney"><img src="https://img.shields.io/npm/v/midjourney.svg?maxAge=3600" alt="npm version" /></a>
	</p>
</div>

## Install

```bash
npm i midjourney
# or
yarn add midjourney
```

## Usage

```typescript
import { Midjourney } from "midjourney";
  const client = new Midjourney({
    ServerId: <string>process.env.SERVER_ID,
    ChannelId: <string>process.env.CHANNEL_ID,
    SalaiToken: <string>process.env.SALAI_TOKEN,
    Debug: true,
    Ws:true,
  });
  await client.Connect();
  const Imagine = await client.Imagine("A little pink elephant", (uri: string, progress:string) => {
   console.log("Imagine", uri, "progress", progress);
  });
  console.log({ Imagine });

  const Variation = await client.Variation({
    index: 2,
    msgId: <string>Imagine.id,
    hash: <string>Imagine.hash,
    flags: Imagine.flags,
    loading: (uri: string, progress: string) => {
      console.log("Variation.loading", uri, "progress", progress);
    },
  });
  console.log({ Variation });
  const Upscale = await client.Upscale({
    index: 2,
    msgId: <string>Variation.id,
    hash: <string>Variation.hash,
    flags: Variation.flags,
    loading: (uri: string, progress: string) => {
      console.log("Upscale.loading", uri, "progress", progress);
    },
  });
  console.log({ Upscale });

```

## Example

To run the included example, you must have [Node.js](https://nodejs.org/en/) installed. Then, run the following commands in the root directory of this project:

1. clone the repository

```bash
git clone https://github.com/erictik/midjourney-api.git
cd midjourney-api
```

2. install dependencies

```bash
yarn
# or npm
npm install
```

3. set the environment variables
  - [How to get your Discord TOKEN:](https://www.androidauthority.com/get-discord-token-3149920/)
  - [Create a server](https://discord.com/blog/starting-your-first-discord-server) and  [Invite Midjourney Bot to Your Server](https://docs.midjourney.com/docs/invite-the-bot)  
  OR [Join my discord server](https://discord.com/invite/GavuGHQbV4)
  - How to get server and channel ids:  
    when you click on a channel in your server in the browser expect to have the follow URL pattern `https://discord.com/channels/$SERVER_ID/$CHANNEL_ID`


```bash
#example variables, please set up yours

export SERVER_ID="1082500871478329374"
export CHANNEL_ID="1094892992281718894"
export SALAI_TOKEN="your-discord-token"
```

Then, run the example with the following command:

```bash
npx tsx example/imagine-ws.ts
```

## route-map
- [x] `/imagine` `variation` `upscale` `reroll` `blend` `zoomout` `vary`
- [x] `/info`
- [x] `/fast ` and `/relax `
- [x] [`/prefer remix`](https://github.com/AI-General/integrate-midjourneyAPI/blob/main/example/prefer-remix.ts) 
- [x] [`variation (remix mode)`](https://github.comAI-General/integrate-midjourneyAPI/blob/main/example/variation-ws.ts)
- [x] `/describe` 
- [x] [`/shorten`](https://github.com/AI-General/integrate-midjourneyAPI/blob/main/example/shorten.ts)
- [x] `/settings` `reset`
- [x] verify human
- [x] [proxy](https://github.com/AI-General/midjourney-discord/blob/main/examples/proxy.ts)
- [x] [niji bot](https://github.comAI-General/midjourney-api/blob/main/example/imagine-niji.ts)
- [x] [custom zoom](https://github.com/AI-General/AI-General/blob/main/example/customzoom.ts)
- [x] autoload command payload
---
## Projects
- [midjourney-ui](https://github.com/AI-General/midjourney-ui/)
- [midjourney-discord](https://github.com/AI-General/midjourney-discord)-bot
- [phrame](https://github.com/jakowenko/phrame)
- [guapitu](https://www.guapitu.com/zh/draw?code=RRXQNF)
---
<a href='https://ko-fi.com/AI-General' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi1.png?v=3' border='0' alt='Buy Me a Coffee' /></a>
## Star History
[![Star History Chart](https://api.star-history.com/svg?repos=erictik/midjourney-api&type=Date)](https://star-history.com/#AI-General/integrate-midjourneyAPI&Date)
